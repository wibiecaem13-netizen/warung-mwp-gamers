const MWP_DEFAULT_MENU = [
  {
    id: "nasi-ayam-critical",
    name: "Nasi Ayam Critical",
    description: "Ayam crispy saus merah pedas manis, telur, dan nasi pulen full energi.",
    price: 18000,
    role: "core",
    roleLabel: "Core"
  },
  {
    id: "mie-boost-xp",
    name: "Mie Boost XP",
    description: "Mie gurih smoky dengan topping sosis, bakso, dan chili oil signature.",
    price: 16000,
    role: "support",
    roleLabel: "Support"
  },
  {
    id: "rice-bowl-patriot",
    name: "Rice Bowl Patriot",
    description: "Beef blackpepper, jagung manis, dan saus creamy biru-putih-merah style MWP.",
    price: 22000,
    role: "tank",
    roleLabel: "Tank"
  },
  {
    id: "es-soda-headshot",
    name: "Es Soda Headshot",
    description: "Mocktail soda segar dengan layer warna merah, putih, dan biru yang nyala.",
    price: 12000,
    role: "sniper",
    roleLabel: "Sniper"
  }
];

const ROLE_LABELS = {
  core: "Core",
  support: "Support",
  tank: "Tank",
  sniper: "Sniper"
};

const STORAGE_KEYS = {
  menu: "mwp_menu_items",
  adminSession: "mwp_admin_session_local"
};

const MENU_SYNC_CHANNEL = "mwp-menu-sync";

const ADMIN_CREDENTIALS = {
  username: "admin",
  password: "mwp123"
};

function roleToLabel(role) {
  return ROLE_LABELS[role] || "Special";
}

function normalizeMenu(items) {
  if (!Array.isArray(items)) {
    return [];
  }

  return items.map((item) => ({
    ...item,
    roleLabel: item.roleLabel || roleToLabel(item.role)
  }));
}

function cloneDefaults() {
  return normalizeMenu(MWP_DEFAULT_MENU).map((item) => ({ ...item }));
}

function canUseLocalStorage() {
  try {
    return typeof window !== "undefined" && typeof window.localStorage !== "undefined";
  } catch (error) {
    return false;
  }
}

function readLocalMenu() {
  if (!canUseLocalStorage()) {
    return cloneDefaults();
  }

  const rawMenu = window.localStorage.getItem(STORAGE_KEYS.menu);
  if (!rawMenu) {
    const defaults = cloneDefaults();
    writeLocalMenu(defaults);
    return defaults;
  }

  try {
    const parsed = JSON.parse(rawMenu);
    const normalized = normalizeMenu(parsed);

    if (!normalized.length) {
      throw new Error("Empty local menu");
    }

    return normalized;
  } catch (error) {
    const defaults = cloneDefaults();
    writeLocalMenu(defaults);
    return defaults;
  }
}

function writeLocalMenu(menu) {
  if (!canUseLocalStorage()) {
    return;
  }

  window.localStorage.setItem(STORAGE_KEYS.menu, JSON.stringify(normalizeMenu(menu)));
}

function canUseBroadcastChannel() {
  return typeof window !== "undefined" && typeof window.BroadcastChannel === "function";
}

let menuBroadcastChannel;

function getMenuBroadcastChannel() {
  if (!canUseBroadcastChannel()) {
    return null;
  }

  if (!menuBroadcastChannel) {
    menuBroadcastChannel = new window.BroadcastChannel(MENU_SYNC_CHANNEL);
  }

  return menuBroadcastChannel;
}

function notifyMenuChanged(source = "local") {
  if (typeof window === "undefined") {
    return;
  }

  const detail = {
    source,
    timestamp: Date.now()
  };

  window.dispatchEvent(new CustomEvent("mwp:menu-changed", { detail }));
  getMenuBroadcastChannel()?.postMessage(detail);
}

function readLocalSession() {
  if (!canUseLocalStorage()) {
    return false;
  }

  return window.localStorage.getItem(STORAGE_KEYS.adminSession) === "true";
}

function writeLocalSession(authenticated) {
  if (!canUseLocalStorage()) {
    return;
  }

  window.localStorage.setItem(STORAGE_KEYS.adminSession, authenticated ? "true" : "false");
}

async function hasReachableApi() {
  if (typeof window === "undefined" || typeof window.fetch !== "function") {
    return false;
  }

  try {
    const response = await fetch("/api/menu", {
      method: "GET",
      credentials: "same-origin",
      cache: "no-store"
    });
    return response.ok;
  } catch (error) {
    return false;
  }
}

let apiModePromise;

async function useApiMode() {
  if (!apiModePromise) {
    apiModePromise = hasReachableApi();
  }

  return apiModePromise;
}

async function apiRequest(url, options = {}) {
  const response = await fetch(url, {
    credentials: "same-origin",
    headers: {
      "Content-Type": "application/json",
      ...(options.headers || {})
    },
    ...options
  });

  const contentType = response.headers.get("content-type") || "";
  const payload = contentType.includes("application/json")
    ? await response.json()
    : await response.text();

  if (!response.ok) {
    const message = typeof payload === "string"
      ? payload
      : payload.detail || "Request gagal";
    throw new Error(message);
  }

  return payload;
}

async function getMenu() {
  if (await useApiMode()) {
    return normalizeMenu(await apiRequest("/api/menu"));
  }

  return readLocalMenu();
}

async function getAdminSession() {
  if (await useApiMode()) {
    return apiRequest("/api/admin/session");
  }

  return { authenticated: readLocalSession() };
}

async function login(username, password) {
  if (await useApiMode()) {
    return apiRequest("/api/admin/login", {
      method: "POST",
      body: JSON.stringify({ username, password })
    });
  }

  if (username !== ADMIN_CREDENTIALS.username || password !== ADMIN_CREDENTIALS.password) {
    throw new Error("Login gagal. Pakai username admin dan password mwp123.");
  }

  writeLocalSession(true);
  return { authenticated: true };
}

async function logout() {
  if (await useApiMode()) {
    return apiRequest("/api/admin/logout", {
      method: "POST"
    });
  }

  writeLocalSession(false);
  return { authenticated: false };
}

async function createMenuItem(item) {
  if (await useApiMode()) {
    const result = await apiRequest("/api/menu", {
      method: "POST",
      body: JSON.stringify(item)
    });
    notifyMenuChanged("api");
    return result;
  }

  if (!readLocalSession()) {
    throw new Error("Akses admin ditolak. Login dulu.");
  }

  const menu = readLocalMenu();
  if (menu.some((menuItem) => menuItem.id === item.id)) {
    throw new Error("ID menu sudah ada. Pakai nama lain.");
  }

  const nextMenu = [...menu, normalizeMenu([item])[0]];
  writeLocalMenu(nextMenu);
  notifyMenuChanged("local");
  return nextMenu;
}

async function updateMenuItem(id, item) {
  if (await useApiMode()) {
    const result = await apiRequest(`/api/menu/${id}`, {
      method: "PUT",
      body: JSON.stringify(item)
    });
    notifyMenuChanged("api");
    return result;
  }

  if (!readLocalSession()) {
    throw new Error("Akses admin ditolak. Login dulu.");
  }

  const menu = readLocalMenu();
  const itemIndex = menu.findIndex((menuItem) => menuItem.id === id);

  if (itemIndex === -1) {
    throw new Error("Menu tidak ditemukan.");
  }

  const nextMenu = [...menu];
  nextMenu[itemIndex] = {
    ...normalizeMenu([item])[0],
    id
  };
  writeLocalMenu(nextMenu);
  notifyMenuChanged("local");
  return nextMenu;
}

async function deleteMenuItem(id) {
  if (await useApiMode()) {
    const result = await apiRequest(`/api/menu/${id}`, {
      method: "DELETE"
    });
    notifyMenuChanged("api");
    return result;
  }

  if (!readLocalSession()) {
    throw new Error("Akses admin ditolak. Login dulu.");
  }

  const menu = readLocalMenu();
  const filteredMenu = menu.filter((menuItem) => menuItem.id !== id);

  if (filteredMenu.length === menu.length) {
    throw new Error("Menu tidak ditemukan.");
  }

  const nextMenu = filteredMenu.length ? filteredMenu : cloneDefaults();
  writeLocalMenu(nextMenu);
  notifyMenuChanged("local");
  return nextMenu;
}

async function getAiStatus() {
  if (!(await useApiMode())) {
    return {
      enabled: false,
      model: null,
      detail: "AI butuh FastAPI mode. Jalankan server lokal dulu."
    };
  }

  return apiRequest("/api/ai/status");
}

async function askMenuAssistant(payload) {
  if (!(await useApiMode())) {
    throw new Error("AI chat butuh FastAPI mode. Jalankan server lokal dulu.");
  }

  return apiRequest("/api/ai/menu-chat", {
    method: "POST",
    body: JSON.stringify(payload)
  });
}

async function generateMenuDraft(brief) {
  if (!(await useApiMode())) {
    throw new Error("AI admin helper butuh FastAPI mode. Jalankan server lokal dulu.");
  }

  return apiRequest("/api/ai/menu-draft", {
    method: "POST",
    body: JSON.stringify({ brief })
  });
}

function subscribeToMenuChanges(callback) {
  if (typeof window === "undefined" || typeof callback !== "function") {
    return () => {};
  }

  const handleStorage = (event) => {
    if (event.key && event.key !== STORAGE_KEYS.menu) {
      return;
    }

    callback({
      source: "storage",
      timestamp: Date.now()
    });
  };

  const handleCustom = (event) => {
    callback(event.detail || {
      source: "custom",
      timestamp: Date.now()
    });
  };

  const channel = getMenuBroadcastChannel();
  const handleBroadcast = (event) => {
    callback(event.data || {
      source: "broadcast",
      timestamp: Date.now()
    });
  };

  window.addEventListener("storage", handleStorage);
  window.addEventListener("mwp:menu-changed", handleCustom);
  channel?.addEventListener("message", handleBroadcast);

  return () => {
    window.removeEventListener("storage", handleStorage);
    window.removeEventListener("mwp:menu-changed", handleCustom);
    channel?.removeEventListener("message", handleBroadcast);
  };
}

window.MenuStore = {
  defaults: cloneDefaults(),
  roleToLabel,
  getMenu,
  getAdminSession,
  login,
  logout,
  createMenuItem,
  updateMenuItem,
  deleteMenuItem,
  getAiStatus,
  askMenuAssistant,
  generateMenuDraft,
  subscribeToMenuChanges
};
