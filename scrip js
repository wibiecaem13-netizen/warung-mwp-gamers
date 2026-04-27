const specials = [
  "Hari ini buff kamu: Nasi Ayam Critical + Es Soda Headshot.",
  "Drop epic hari ini: Rice Bowl Patriot buat push rank lebih santai.",
  "Quest makan aktif: Mie Boost XP cocok buat sesi grind malam.",
  "Combo hoki: Paket Sultan Ranked lagi jadi favorit basecamp."
];

const specialButton = document.getElementById("dailySpecialBtn");
const form = document.querySelector(".order-form");
const formMessage = document.getElementById("formMessage");
const quickAddButton = document.getElementById("quickAddBtn");
const quickMenu = document.getElementById("quickMenu");
const customerName = document.getElementById("customerName");
const orderNote = document.getElementById("orderNote");
const cartItems = document.getElementById("cartItems");
const cartCount = document.getElementById("cartCount");
const cartTotal = document.getElementById("cartTotal");
const gojekLink = document.getElementById("gojekLink");
const grabLink = document.getElementById("grabLink");
const menuGrid = document.getElementById("menuGrid");
const musicToggle = document.getElementById("musicToggle");
const bgMusic = document.getElementById("bgMusic");
const musicState = document.getElementById("musicState");
const musicTime = document.getElementById("musicTime");
const musicProgress = document.getElementById("musicProgress");
const musicVolume = document.getElementById("musicVolume");
const wallpaperRotator = document.getElementById("wallpaperRotator");
const heroCard = document.querySelector(".hero-card");
const cartPanel = document.querySelector(".cart-panel");
const heroWhatsAppBtn = document.getElementById("heroWhatsAppBtn");
const scrollProgress = document.getElementById("scrollProgress");
const breakingNewsCarousel = document.querySelector("[data-news-carousel]");
const foodSlider = document.querySelector("[data-food-slider]");
const miniGameArena = document.getElementById("miniGameArena");
const miniGameCanvas = document.getElementById("miniGameCanvas");
const miniGameOverlayText = document.getElementById("miniGameOverlayText");
const miniGameScore = document.getElementById("miniGameScore");
const miniGameHp = document.getElementById("miniGameHp");
const miniGameTimer = document.getElementById("miniGameTimer");
const miniGameStatus = document.getElementById("miniGameStatus");
const miniGameStartBtn = document.getElementById("miniGameStartBtn");
const miniGameResetBtn = document.getElementById("miniGameResetBtn");
const miniGameBuildTools = document.querySelectorAll("[data-build-tool]");
const WHATSAPP_NUMBER = "6281328440958";

const GAME_WALLPAPERS = [
  {
    title: "Free Fire Neon Rooftop",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/82fe305f7dbb9f25e68996f8f719e576.jpg",
    position: "center center"
  },
  {
    title: "Free Fire City Run",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/c23d656a45bc5c75cd77d53065605fe0.jpg",
    position: "center center"
  },
  {
    title: "Free Fire Cyber Duo",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/2d6e7a11b79218c9b29167f77a9b92eb.jpg",
    position: "center center"
  },
  {
    title: "Free Fire Mask Squad",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/aa959aa3d8790d3a44f7f20f16adfa01.jpg",
    position: "center center"
  },
  {
    title: "Free Fire Music Stage",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/897ff6f29088b65b78d1d361d8d13ac4.jpg",
    position: "center center"
  },
  {
    title: "Free Fire Cyber Rain",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/3339313cfb446d61ce907b5efc2b4fd7.jpg",
    position: "center center"
  },
  {
    title: "Free Fire Pulse Arena",
    url: "https://dl.dir.freefiremobile.com/common/web_event/official2.ff.garena.all/202210/09c0ec228dbd9b2a264fb5509fab8b11.jpg",
    position: "center center"
  },
  {
    title: "Forza Horizon 5 Explore The Horizon",
    url: "https://cdn.forza.net/strapi-uploads/assets/small_FH_5_Series21_HUMMER_EV_21_16x9_3840x2160_WM_7b7010a1d0.jpg",
    position: "center center"
  },
  {
    title: "Forza Horizon 5 Forest Ride",
    url: "https://cdn.forza.net/strapi-uploads/assets/small_FH_5_Series21_Forest_35_16x9_3840x2160_WM_9b0d5dd1d0.jpg",
    position: "center center"
  },
  {
    title: "Forza Horizon 5 Night Photo",
    url: "https://cdn.forza.net/strapi-uploads/assets/small_FH_5_Series21_Surboard_36_16x9_3840x2160_WM_e16891331d.jpg",
    position: "center center"
  },
  {
    title: "Forza Horizon 5 Oval Track",
    url: "https://cdn.forza.net/strapi-uploads/assets/small_FH_5_Series21_Oval_Stadium_81_16x9_3840x2160_WM_7b4bc6d3a2.jpg",
    position: "center center"
  },
  {
    title: "Forza Horizon 5 Rocky Trail",
    url: "https://cdn.forza.net/strapi-uploads/assets/small_FH_5_Series21_Rock_Crawler_88_16x9_3840x2160_WM_4d7f6a1b6d.jpg",
    position: "center center"
  }
];

let menuItems = [];
let cart = [];
let isMusicPlaying = false;
let autoplayAttempted = false;
let sectionObserver;
let itemObserver;
let statObserver;
let lastCartQty = 0;
let latestMenuSignature = "";
let musicVisualFrame = 0;
let lastMusicPulse = 0;
let lastMusicBeatAt = 0;
let musicBeatTimer = 0;
let wallpaperSlides = [];
let activeWallpaperIndex = 0;
let activeWallpaperSlideIndex = 0;
let wallpaperTimer = 0;
let cursorTrailIndex = 0;
let miniGameState = {
  running: false,
  scrap: 120,
  baseHp: 100,
  wave: 1,
  kills: 0,
  animationId: 0,
  selectedTool: "turret",
  grid: { cols: 18, rows: 10, cellSize: 40, offsetX: 0, offsetY: 0 },
  turrets: [],
  walls: [],
  bullets: [],
  enemies: [],
  effects: [],
  pointer: { x: 360, y: 200, inside: false, col: -1, row: -1 },
  spawnQueue: 0,
  spawnCooldown: 0,
  waveActive: false,
  baseFlash: 0,
  screenShake: 0,
  wavePulse: 0,
  ambientCooldown: 0,
  lastFrameAt: 0
};

function formatRupiah(value) {
  return new Intl.NumberFormat("id-ID", {
    style: "currency",
    currency: "IDR",
    maximumFractionDigits: 0
  }).format(value);
}

function setStatusMessage(message) {
  if (formMessage) {
    formMessage.textContent = message;
  }
}

function setMiniGameStatus(message) {
  if (miniGameStatus) {
    miniGameStatus.textContent = message;
  }
}

function pulseElement(element, className = "is-pulsing", duration = 560) {
  if (!element) {
    return;
  }

  element.classList.remove(className);
  void element.offsetWidth;
  element.classList.add(className);

  window.setTimeout(() => {
    element.classList.remove(className);
  }, duration);
}

function burstButton(button, event) {
  if (!button) {
    return;
  }

  const rect = button.getBoundingClientRect();
  const x = event ? event.clientX - rect.left : rect.width / 2;
  const y = event ? event.clientY - rect.top : rect.height / 2;

  button.style.setProperty("--burst-x", `${x}px`);
  button.style.setProperty("--burst-y", `${y}px`);
  button.classList.remove("is-bursting");
  void button.offsetWidth;
  button.classList.add("is-bursting");

  window.setTimeout(() => {
    button.classList.remove("is-bursting");
  }, 540);
}

function setBassVisuals(level) {
  const nextLevel = Math.max(0, Math.min(level, 1));
  const root = document.documentElement;
  const glowLevel = 0.18 + (nextLevel * 0.82);
  const scaleLevel = 1 + (nextLevel * 0.12);
  const shiftLevel = `${(nextLevel * -18).toFixed(2)}px`;

  root.style.setProperty("--bass-energy", nextLevel.toFixed(3));
  root.style.setProperty("--bass-glow", glowLevel.toFixed(3));
  root.style.setProperty("--bass-scale", scaleLevel.toFixed(3));
  root.style.setProperty("--bass-shift", shiftLevel);
}

function formatDuration(seconds) {
  if (!Number.isFinite(seconds) || seconds < 0) {
    return "00:00";
  }

  const totalSeconds = Math.floor(seconds);
  const minutes = Math.floor(totalSeconds / 60);
  const remainingSeconds = totalSeconds % 60;

  return `${String(minutes).padStart(2, "0")}:${String(remainingSeconds).padStart(2, "0")}`;
}

function setMusicPulse(level) {
  const normalized = Math.max(0, Math.min(level, 1));
  document.documentElement.style.setProperty("--music-pulse", normalized.toFixed(3));
}

function preloadWallpaper(url) {
  if (!url) {
    return;
  }

  const image = new Image();
  image.src = url;
}

function applyWallpaperToSlide(slide, wallpaper) {
  if (!slide || !wallpaper) {
    return;
  }

  slide.style.backgroundImage = `url("${wallpaper.url}")`;
  slide.style.backgroundPosition = wallpaper.position || "center center";
}

function rotateWallpaper(initial = false) {
  if (!wallpaperSlides.length || !GAME_WALLPAPERS.length) {
    return;
  }

  const nextWallpaper = GAME_WALLPAPERS[activeWallpaperIndex];
  const nextSlide = wallpaperSlides[activeWallpaperSlideIndex];

  applyWallpaperToSlide(nextSlide, nextWallpaper);
  wallpaperSlides.forEach((slide, index) => {
    slide.classList.toggle("is-active", index === activeWallpaperSlideIndex);
  });

  const preloadIndex = (activeWallpaperIndex + 1) % GAME_WALLPAPERS.length;
  preloadWallpaper(GAME_WALLPAPERS[preloadIndex].url);

  activeWallpaperIndex = preloadIndex;
  activeWallpaperSlideIndex = activeWallpaperSlideIndex === 0 ? 1 : 0;

  if (!initial) {
    document.body.classList.add("bass-hit");
    window.setTimeout(() => document.body.classList.remove("bass-hit"), 220);
  }
}

function setupWallpaperRotator() {
  if (!wallpaperRotator || wallpaperSlides.length) {
    return;
  }

  wallpaperSlides = Array.from(wallpaperRotator.querySelectorAll(".wallpaper-slide"));
  if (!wallpaperSlides.length || !GAME_WALLPAPERS.length) {
    return;
  }

  rotateWallpaper(true);

  wallpaperTimer = window.setInterval(() => {
    rotateWallpaper();
  }, 8500);
}

function triggerMusicBeat() {
  const now = performance.now();
  if (now - lastMusicBeatAt < 180) {
    return;
  }

  lastMusicBeatAt = now;
  document.body.classList.add("bass-hit");

  if (musicBeatTimer) {
    window.clearTimeout(musicBeatTimer);
  }

  musicBeatTimer = window.setTimeout(() => {
    document.body.classList.remove("bass-hit");
    musicBeatTimer = 0;
  }, 140);
}

function updateVolumeVisual() {
  if (!bgMusic) {
    return;
  }

  const volumePercent = Math.round(bgMusic.volume * 100);
  document.documentElement.style.setProperty("--music-volume-level", `${volumePercent}%`);
  if (musicVolume) {
    musicVolume.value = String(volumePercent);
  }
}

function updateMusicProgress() {
  if (!bgMusic) {
    return;
  }

  const duration = Number.isFinite(bgMusic.duration) ? bgMusic.duration : 0;
  const currentTime = Number.isFinite(bgMusic.currentTime) ? bgMusic.currentTime : 0;
  const progressPercent = duration > 0 ? (currentTime / duration) * 100 : 0;

  document.documentElement.style.setProperty("--music-progress", `${Math.min(progressPercent, 100).toFixed(2)}%`);

  if (musicTime) {
    musicTime.textContent = `${formatDuration(currentTime)} / ${formatDuration(duration)}`;
  }
}

function updateMusicStatus() {
  if (!musicState || !bgMusic) {
    return;
  }

  if (isMusicPlaying) {
    musicState.textContent = "Playing";
    return;
  }

  if (bgMusic.ended) {
    musicState.textContent = "Selesai";
    return;
  }

  musicState.textContent = bgMusic.currentTime > 0 ? "Paused" : "Standby";
}

function stopBassTracking() {
  if (musicVisualFrame) {
    window.cancelAnimationFrame(musicVisualFrame);
    musicVisualFrame = 0;
  }

  if (musicBeatTimer) {
    window.clearTimeout(musicBeatTimer);
    musicBeatTimer = 0;
  }

  document.body.classList.remove("music-active");
  document.body.classList.remove("bass-hit");
  lastMusicPulse = 0;
  setMusicPulse(0);
  setBassVisuals(0);
}

function animateStatValue(element) {
  if (!element || element.dataset.animated === "true") {
    return;
  }

  const targetValue = Number(element.dataset.countTo);
  const suffix = element.dataset.countSuffix || "";

  if (!Number.isFinite(targetValue)) {
    element.dataset.animated = "true";
    return;
  }

  element.dataset.animated = "true";
  element.classList.remove("is-counting");
  void element.offsetWidth;
  element.classList.add("is-counting");

  const startTime = performance.now();
  const duration = 1100;

  const tick = (now) => {
    const progress = Math.min((now - startTime) / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3);
    const currentValue = Math.round(targetValue * eased);
    element.textContent = `${currentValue}${suffix}`;

    if (progress < 1) {
      window.requestAnimationFrame(tick);
      return;
    }

    element.textContent = `${targetValue}${suffix}`;
    window.setTimeout(() => {
      element.classList.remove("is-counting");
    }, 680);
  };

  window.requestAnimationFrame(tick);
}

function setupMagneticButtons() {
  const magneticTargets = document.querySelectorAll(
    ".primary-btn, .secondary-btn, .cta-link, .add-cart-btn, .delivery-btn, .music-toggle, .danger-btn"
  );

  magneticTargets.forEach((element) => {
    if (element.dataset.magnetBound === "true") {
      return;
    }

    element.dataset.magnetBound = "true";

    element.addEventListener("pointerenter", () => {
      document.body.classList.add("cursor-hover");
    });

    element.addEventListener("pointermove", (event) => {
      const rect = element.getBoundingClientRect();
      const offsetX = event.clientX - rect.left - (rect.width / 2);
      const offsetY = event.clientY - rect.top - (rect.height / 2);
      const shiftX = offsetX * 0.14;
      const shiftY = offsetY * 0.16;

      element.style.transform = `translate3d(${shiftX}px, ${shiftY}px, 0) scale(1.04)`;
    });

    element.addEventListener("pointerleave", () => {
      element.style.transform = "";
      document.body.classList.remove("cursor-hover");
    });
  });
}

function setupCursorEffects() {
  if (!window.matchMedia("(pointer: fine)").matches || window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
    return;
  }

  const layer = document.createElement("div");
  const orb = document.createElement("div");
  const dot = document.createElement("div");
  const sparks = Array.from({ length: 8 }, () => {
    const spark = document.createElement("span");
    spark.className = "cursor-spark";
    layer.appendChild(spark);
    return spark;
  });
  const waves = Array.from({ length: 3 }, () => {
    const wave = document.createElement("span");
    wave.className = "cursor-wave";
    layer.appendChild(wave);
    return wave;
  });

  let pointerX = window.innerWidth / 2;
  let pointerY = window.innerHeight / 2;
  let orbX = pointerX;
  let orbY = pointerY;
  let dotX = pointerX;
  let dotY = pointerY;
  let animationFrame = 0;
  let lastSparkAt = 0;
  let waveIndex = 0;

  layer.className = "cursor-fx-layer";
  orb.className = "cursor-orb";
  dot.className = "cursor-dot";
  layer.append(orb, dot);
  document.body.appendChild(layer);
  document.body.classList.add("cursor-fx-active");

  const animateCursor = () => {
    orbX += (pointerX - orbX) * 0.38;
    orbY += (pointerY - orbY) * 0.38;
    dotX += (pointerX - dotX) * 0.72;
    dotY += (pointerY - dotY) * 0.72;

    orb.style.transform = `translate3d(${orbX}px, ${orbY}px, 0)`;
    dot.style.transform = `translate3d(${dotX}px, ${dotY}px, 0)`;
    animationFrame = window.requestAnimationFrame(animateCursor);
  };

  const spawnSpark = (x, y) => {
    const now = performance.now();
    if (now - lastSparkAt < 20) {
      return;
    }

    lastSparkAt = now;
    const spark = sparks[cursorTrailIndex % sparks.length];
    cursorTrailIndex += 1;
    const driftX = `${(Math.random() - 0.5) * 18}px`;
    const driftY = `${(Math.random() - 0.5) * 18}px`;

    spark.classList.remove("is-active");
    spark.style.left = `${x}px`;
    spark.style.top = `${y}px`;
    spark.style.setProperty("--spark-x", driftX);
    spark.style.setProperty("--spark-y", driftY);
    void spark.offsetWidth;
    spark.classList.add("is-active");
  };

  const spawnWave = (x, y) => {
    const wave = waves[waveIndex % waves.length];
    waveIndex += 1;
    wave.classList.remove("is-active");
    wave.style.left = `${x}px`;
    wave.style.top = `${y}px`;
    void wave.offsetWidth;
    wave.classList.add("is-active");
  };

  const handlePointerMove = (event) => {
    pointerX = event.clientX;
    pointerY = event.clientY;
    dotX = pointerX;
    dotY = pointerY;
    dot.style.transform = `translate3d(${dotX}px, ${dotY}px, 0)`;
    spawnSpark(pointerX, pointerY);
  };

  document.addEventListener("pointermove", handlePointerMove);
  document.addEventListener("pointerdown", () => {
    document.body.classList.add("cursor-pressed");
    spawnWave(pointerX, pointerY);
  });
  document.addEventListener("pointerup", () => {
    document.body.classList.remove("cursor-pressed");
  });
  document.addEventListener("pointerleave", () => {
    document.body.classList.remove("cursor-hover");
    document.body.classList.remove("cursor-pressed");
  });

  animateCursor();

  window.addEventListener("beforeunload", () => {
    if (animationFrame) {
      window.cancelAnimationFrame(animationFrame);
    }
  }, { once: true });
}

function enablePanelSpotlight(panel) {
  if (!panel || panel.dataset.spotlightBound === "true") {
    return;
  }

  panel.dataset.spotlightBound = "true";

  panel.addEventListener("pointermove", (event) => {
    const rect = panel.getBoundingClientRect();
    panel.style.setProperty("--panel-spotlight-x", `${event.clientX - rect.left}px`);
    panel.style.setProperty("--panel-spotlight-y", `${event.clientY - rect.top}px`);
  });

  panel.addEventListener("pointerleave", () => {
    panel.style.removeProperty("--panel-spotlight-x");
    panel.style.removeProperty("--panel-spotlight-y");
  });
}

function startSafeMusicVisuals() {
  if (!bgMusic || musicVisualFrame) {
    return;
  }

  const animateMusic = () => {
    if (!bgMusic || bgMusic.paused) {
      musicVisualFrame = 0;
      document.body.classList.remove("music-active");
      setMusicPulse(0);
      setBassVisuals(0);
      return;
    }

    const playbackTime = bgMusic.currentTime || 0;
    const volumeFactor = Math.max(bgMusic.volume, 0.2);
    const fallbackPulse = (
      ((Math.sin(playbackTime * 2.9) + 1) * 0.5 * 0.5) +
      ((Math.sin(playbackTime * 5.8 + 0.9) + 1) * 0.5 * 0.36) +
      ((Math.sin(playbackTime * 1.6 + 1.4) + 1) * 0.5 * 0.24)
    ) * volumeFactor;
    const pulseRise = fallbackPulse - lastMusicPulse;

    document.body.classList.add("music-active");
    setMusicPulse(fallbackPulse);
    setBassVisuals(fallbackPulse * 0.9);
    updateMusicProgress();

    if (fallbackPulse > 0.4 && pulseRise > 0.035) {
      triggerMusicBeat();
    }

    lastMusicPulse = fallbackPulse;

    musicVisualFrame = window.requestAnimationFrame(animateMusic);
  };

  animateMusic();
}

function getMenuSignature(items) {
  return JSON.stringify(items);
}

function sanitizeCart() {
  cart = cart.filter((cartItem) => menuItems.some((menuItem) => menuItem.id === cartItem.id));
  cart = cart.map((cartItem) => {
    const updatedMenu = menuItems.find((menuItem) => menuItem.id === cartItem.id);
    return {
      ...cartItem,
      name: updatedMenu.name,
      price: updatedMenu.price
    };
  });
}

function renderMenu() {
  if (!menuGrid) {
    return;
  }

  menuGrid.innerHTML = menuItems.map((item, index) => `
    <article
      class="menu-card"
      data-animate-item
      data-reveal="${index % 3 === 0 ? "left" : index % 3 === 1 ? "up" : "right"}"
      style="--stagger-delay: ${index * 90}ms; --float-delay: ${index * 0.18}s;"
    >
      <span class="role role-${item.role}">${item.roleLabel}</span>
      <h3>${item.name}</h3>
      <p>${item.description}</p>
      <div class="menu-card-footer">
        <strong>${formatRupiah(item.price)}</strong>
        <button
          class="add-cart-btn"
          type="button"
          data-id="${item.id}"
        >
          + Keranjang
        </button>
      </div>
    </article>
  `).join("");

  menuGrid.querySelectorAll(".add-cart-btn").forEach((button) => {
    button.addEventListener("click", (event) => {
      burstButton(button, event);
      addToCart(button.dataset.id);
    });
  });

  enableTiltEffects(menuGrid.querySelectorAll(".menu-card"));
  setupMagneticButtons();
  observeAnimatedItems(menuGrid.querySelectorAll("[data-animate-item]"));
}

function renderQuickMenuOptions() {
  if (!quickMenu) {
    return;
  }

  quickMenu.innerHTML = menuItems.map((item) => `
    <option value="${item.id}">${item.name} - ${formatRupiah(item.price)}</option>
  `).join("");
}

function buildOrderMessage() {
  if (!cart.length) {
    const buyer = customerName?.value.trim();
    const note = orderNote?.value.trim();

    return [
      `Halo Warung Bu Asih, saya ${buyer || "mau pesan"}.`,
      `Menu pilihan: ${quickMenu?.selectedOptions?.[0]?.textContent || "Belum dipilih"}`,
      note ? `Catatan: ${note}` : "Catatan: -"
    ].join("\n");
  }

  const buyer = customerName?.value.trim() || "Customer";
  const note = orderNote?.value.trim();
  const lines = cart.map((item, index) => `${index + 1}. ${item.name} x${item.qty} - ${formatRupiah(item.price * item.qty)}`);
  const total = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);

  return [
    `Halo Warung Bu Asih, saya ${buyer} mau pesan:`,
    ...lines,
    `Total sementara: ${formatRupiah(total)}`,
    note ? `Catatan: ${note}` : "Catatan: -"
  ].join("\n");
}

function buildWhatsAppUrl(message) {
  return `https://wa.me/${WHATSAPP_NUMBER}?text=${encodeURIComponent(message)}`;
}

function openWhatsAppOrder(message) {
  const url = buildWhatsAppUrl(message);
  window.open(url, "_blank", "noopener");
}

function updateDeliveryLinks() {
  if (!gojekLink || !grabLink) {
    return;
  }

  const encodedMessage = encodeURIComponent(buildOrderMessage());
  gojekLink.href = `https://gofood.link/a/${encodedMessage}`;
  grabLink.href = `https://food.grab.com/id/in/merchant-search?q=${encodedMessage}`;

  if (heroWhatsAppBtn) {
    heroWhatsAppBtn.href = buildWhatsAppUrl(buildOrderMessage());
  }
}

function renderCart() {
  if (!cartItems || !cartCount || !cartTotal) {
    return;
  }

  if (!cart.length) {
    cartItems.innerHTML = '<p class="cart-empty">Keranjang masih kosong. Loot makanan dulu.</p>';
  } else {
    cartItems.innerHTML = cart.map((item, index) => `
      <article
        class="cart-item"
        data-animate-item
        data-reveal="${index % 2 === 0 ? "left" : "right"}"
        style="--stagger-delay: ${index * 70}ms; --float-delay: ${index * 0.16}s;"
      >
        <div class="cart-row">
          <strong>${item.name}</strong>
          <button type="button" data-remove-index="${index}">Hapus</button>
        </div>
        <p class="cart-note">${item.qty}x ${formatRupiah(item.price)}</p>
      </article>
    `).join("");
  }

  const totalQty = cart.reduce((sum, item) => sum + item.qty, 0);
  const totalPrice = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);

  cartCount.textContent = `${totalQty} item`;
  cartTotal.textContent = formatRupiah(totalPrice);

  if (cartCount && totalQty > lastCartQty) {
    cartCount.classList.remove("is-bumping");
    void cartCount.offsetWidth;
    cartCount.classList.add("is-bumping");
    window.setTimeout(() => cartCount.classList.remove("is-bumping"), 450);
  }
  lastCartQty = totalQty;

  cartItems.querySelectorAll("[data-remove-index]").forEach((button) => {
    button.addEventListener("click", () => {
      const index = Number(button.dataset.removeIndex);
      cart.splice(index, 1);
      renderCart();
      updateDeliveryLinks();
    });
  });

  observeAnimatedItems(cartItems.querySelectorAll("[data-animate-item]"));
}

function addToCart(menuId) {
  const selectedMenu = menuItems.find((item) => item.id === menuId);
  if (!selectedMenu) {
    return;
  }

  const existingItem = cart.find((item) => item.id === menuId);

  if (existingItem) {
    existingItem.qty += 1;
  } else {
    cart.push({
      id: selectedMenu.id,
      name: selectedMenu.name,
      price: selectedMenu.price,
      qty: 1
    });
  }

  setStatusMessage(`${selectedMenu.name} masuk keranjang. Tinggal lanjut checkout squad.`);
  renderCart();
  updateDeliveryLinks();
  pulseElement(cartPanel);
}

async function refreshMenuState(showUpdateMessage = false) {
  try {
    const fetchedMenu = await window.MenuStore.getMenu();
    const nextSignature = getMenuSignature(fetchedMenu);
    const hasChanged = nextSignature !== latestMenuSignature;

    menuItems = fetchedMenu;
    latestMenuSignature = nextSignature;
    sanitizeCart();
    renderMenu();
    renderQuickMenuOptions();
    renderCart();
    updateDeliveryLinks();

    if (showUpdateMessage && hasChanged) {
      setStatusMessage("Menu update terdeteksi. Harga dan item terbaru sudah sinkron.");
    }
  } catch (error) {
    setStatusMessage("Gagal ambil menu. Coba refresh halaman atau cek koneksi.");
  }
}

function setupMenuRealtimeSync() {
  const triggerRefresh = () => {
    refreshMenuState(true);
  };

  window.MenuStore.subscribeToMenuChanges?.(triggerRefresh);
  window.addEventListener("focus", triggerRefresh);
  document.addEventListener("visibilitychange", () => {
    if (!document.hidden) {
      triggerRefresh();
    }
  });
}

function updateMusicButton() {
  if (!musicToggle) {
    return;
  }

  musicToggle.textContent = isMusicPlaying ? "Pause Musik" : "Nyalain Musik";
  musicToggle.classList.toggle("is-playing", isMusicPlaying);
  updateMusicStatus();
}

function enableTiltEffects(elements) {
  elements.forEach((element) => {
    if (element.dataset.tiltBound === "true") {
      return;
    }

    element.dataset.tiltBound = "true";

    element.addEventListener("pointermove", (event) => {
      const rect = element.getBoundingClientRect();
      const offsetX = event.clientX - rect.left;
      const offsetY = event.clientY - rect.top;
      const rotateY = ((offsetX / rect.width) - 0.5) * 12;
      const rotateX = (0.5 - (offsetY / rect.height)) * 12;

      element.style.transform = `translateY(-8px) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
      element.style.setProperty("--spotlight-x", `${offsetX}px`);
      element.style.setProperty("--spotlight-y", `${offsetY}px`);
    });

    element.addEventListener("pointerleave", () => {
      element.style.transform = "";
      element.style.removeProperty("--spotlight-x");
      element.style.removeProperty("--spotlight-y");
    });
  });
}

function setupHeroParallax() {
  const hero = document.querySelector(".hero");
  const heroCopy = document.querySelector(".hero-copy");
  const heroCard = document.querySelector(".hero-card");
  const stickerStage = document.querySelector(".anime-sticker-stage");

  if (!hero || (!heroCopy && !heroCard && !stickerStage)) {
    return;
  }

  hero.addEventListener("pointermove", (event) => {
    const rect = hero.getBoundingClientRect();
    const percentX = (event.clientX - rect.left) / rect.width - 0.5;
    const percentY = (event.clientY - rect.top) / rect.height - 0.5;

    if (heroCopy) {
      heroCopy.style.transform = `translate3d(${percentX * 10}px, ${percentY * 8}px, 0)`;
    }

    if (heroCard) {
      heroCard.style.transform = `translate3d(${percentX * -14}px, ${percentY * -10}px, 0)`;
    }

    if (stickerStage) {
      stickerStage.style.transform = `translate3d(${percentX * -8}px, ${percentY * -6}px, 0) rotateX(${percentY * 4}deg) rotateY(${percentX * -4}deg)`;
    }
  });

  hero.addEventListener("pointerleave", () => {
    if (heroCopy) {
      heroCopy.style.transform = "";
    }

    if (heroCard) {
      heroCard.style.transform = "";
    }

    if (stickerStage) {
      stickerStage.style.transform = "";
    }
  });
}

function setupBreakingNewsCarousel() {
  if (!breakingNewsCarousel) {
    return;
  }

  const list = breakingNewsCarousel.querySelector(".breaking-news-list");
  const items = Array.from(breakingNewsCarousel.querySelectorAll(".breaking-news-item"));
  const dots = Array.from(breakingNewsCarousel.querySelectorAll(".news-dot"));
  const prevButton = breakingNewsCarousel.querySelector("[data-news-prev]");
  const nextButton = breakingNewsCarousel.querySelector("[data-news-next]");
  const idleDelay = 30000;
  const autoDelay = 6000;
  let activeIndex = Math.max(items.findIndex((item) => item.classList.contains("is-active")), 0);
  let idleTimer = 0;
  let autoTimer = 0;
  let dragStartX = 0;
  let dragCurrentX = 0;
  let isDragging = false;
  let suppressClick = false;

  if (!list || items.length < 2) {
    return;
  }

  const stopAuto = () => {
    if (autoTimer) {
      window.clearInterval(autoTimer);
      autoTimer = 0;
    }
  };

  const startAuto = () => {
    stopAuto();
    autoTimer = window.setInterval(() => {
      setActiveNews(activeIndex + 1, "next", false);
    }, autoDelay);
  };

  const armIdleAuto = () => {
    stopAuto();

    if (idleTimer) {
      window.clearTimeout(idleTimer);
    }

    idleTimer = window.setTimeout(startAuto, idleDelay);
  };

  function setActiveNews(nextIndex, direction = "next", markInteraction = true) {
    const normalizedIndex = (nextIndex + items.length) % items.length;
    activeIndex = normalizedIndex;

    items.forEach((item, index) => {
      item.classList.toggle("is-active", index === activeIndex);
      item.classList.toggle("is-prev", direction === "prev" && index !== activeIndex);
    });

    dots.forEach((dot, index) => {
      dot.classList.toggle("is-active", index === activeIndex);
    });

    if (markInteraction) {
      armIdleAuto();
    }
  }

  const goToPrevious = () => setActiveNews(activeIndex - 1, "prev");
  const goToNext = () => setActiveNews(activeIndex + 1, "next");

  prevButton?.addEventListener("click", goToPrevious);
  nextButton?.addEventListener("click", goToNext);

  dots.forEach((dot) => {
    dot.addEventListener("click", () => {
      const nextIndex = Number(dot.dataset.newsDot);
      const direction = nextIndex < activeIndex ? "prev" : "next";
      setActiveNews(nextIndex, direction);
    });
  });

  items.forEach((item) => {
    item.addEventListener("click", (event) => {
      if (suppressClick) {
        event.preventDefault();
        suppressClick = false;
      }
    });
  });

  list.addEventListener("pointerdown", (event) => {
    if (event.button !== undefined && event.button !== 0) {
      return;
    }

    isDragging = true;
    dragStartX = event.clientX;
    dragCurrentX = event.clientX;
    suppressClick = false;
    list.classList.add("is-dragging");
    list.setPointerCapture?.(event.pointerId);
    armIdleAuto();
  });

  list.addEventListener("pointermove", (event) => {
    if (!isDragging) {
      return;
    }

    dragCurrentX = event.clientX;

    if (Math.abs(dragCurrentX - dragStartX) > 8) {
      suppressClick = true;
    }
  });

  const finishDrag = (event) => {
    if (!isDragging) {
      return;
    }

    const deltaX = dragCurrentX - dragStartX;
    isDragging = false;
    list.classList.remove("is-dragging");
    list.releasePointerCapture?.(event.pointerId);

    if (Math.abs(deltaX) > 44) {
      if (deltaX > 0) {
        goToPrevious();
      } else {
        goToNext();
      }
    } else {
      armIdleAuto();
    }
  };

  list.addEventListener("pointerup", finishDrag);
  list.addEventListener("pointercancel", finishDrag);
  breakingNewsCarousel.addEventListener("mouseenter", armIdleAuto);
  breakingNewsCarousel.addEventListener("focusin", armIdleAuto);

  setActiveNews(activeIndex, "next", false);
  armIdleAuto();
}

function setupFoodSlider() {
  if (!foodSlider) {
    return;
  }

  const slides = Array.from(foodSlider.querySelectorAll(".food-slide"));
  const dots = Array.from(foodSlider.querySelectorAll(".food-slider-dots span"));
  if (slides.length < 2) {
    return;
  }

  let activeIndex = Math.max(slides.findIndex((slide) => slide.classList.contains("is-active")), 0);

  const setActiveSlide = (nextIndex) => {
    activeIndex = (nextIndex + slides.length) % slides.length;
    slides.forEach((slide, index) => {
      slide.classList.toggle("is-active", index === activeIndex);
    });
    dots.forEach((dot, index) => {
      dot.classList.toggle("is-active", index === activeIndex);
    });
  };

  setActiveSlide(activeIndex);
  window.setInterval(() => {
    setActiveSlide(activeIndex + 1);
  }, 3600);
}

function setupScrollProgress() {
  if (!scrollProgress) {
    return;
  }

  const updateProgress = () => {
    const scrollableHeight = document.documentElement.scrollHeight - window.innerHeight;
    const ratio = scrollableHeight > 0 ? window.scrollY / scrollableHeight : 0;
    const normalizedRatio = Math.min(Math.max(ratio, 0), 1);
    document.documentElement.style.setProperty("--scroll-progress", `${(normalizedRatio * 100).toFixed(2)}%`);
    document.documentElement.style.setProperty("--scroll-depth", normalizedRatio.toFixed(3));
  };

  updateProgress();
  window.addEventListener("scroll", updateProgress, { passive: true });
  window.addEventListener("resize", updateProgress);
}

function setupAmbientSpotlights() {
  const targets = document.querySelectorAll(".hero, .section, .location-card, .order-form, .cart-panel, .minigame-arena, .minigame-panel");
  targets.forEach((target) => enablePanelSpotlight(target));
}

function setupSectionAnimations() {
  const sections = document.querySelectorAll(".section");
  const featureCards = document.querySelectorAll(".feature-list article");
  const surfaceCards = document.querySelectorAll(".location-card, .order-form, .cart-panel, .minigame-arena, .minigame-panel");
  const sectionReveals = ["up", "left", "right", "up"];
  const itemReveals = ["left", "up", "right"];

  sections.forEach((section, index) => {
    section.setAttribute("data-animate", "");
    section.dataset.reveal = sectionReveals[index % sectionReveals.length];
  });

  featureCards.forEach((card, index) => {
    card.setAttribute("data-animate-item", "");
    card.dataset.reveal = itemReveals[index % itemReveals.length];
    card.style.setProperty("--stagger-delay", `${index * 110}ms`);
  });

  surfaceCards.forEach((card, index) => {
    card.setAttribute("data-animate-item", "");
    card.dataset.reveal = itemReveals[index % itemReveals.length];
    card.style.setProperty("--stagger-delay", `${120 + (index * 90)}ms`);
  });

  if (!("IntersectionObserver" in window)) {
    sections.forEach((section) => section.classList.add("is-visible"));
    featureCards.forEach((card) => card.classList.add("is-visible"));
    surfaceCards.forEach((card) => card.classList.add("is-visible"));
    return;
  }

  sectionObserver = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("is-visible");
        sectionObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.16 });

  sections.forEach((section) => sectionObserver.observe(section));
  observeAnimatedItems(featureCards);
  observeAnimatedItems(surfaceCards);
}

function observeAnimatedItems(elements) {
  if (!elements?.length) {
    return;
  }

  if (!("IntersectionObserver" in window)) {
    elements.forEach((element) => element.classList.add("is-visible"));
    return;
  }

  if (!itemObserver) {
    itemObserver = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible");
          itemObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.18 });
  }

  elements.forEach((element) => itemObserver.observe(element));
}

function setupStatCounters() {
  const statValues = document.querySelectorAll(".stat-value[data-count-to]");

  if (!statValues.length) {
    return;
  }

  if (!("IntersectionObserver" in window)) {
    statValues.forEach(animateStatValue);
    return;
  }

  if (!statObserver) {
    statObserver = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          animateStatValue(entry.target);
          statObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.5 });
  }

  statValues.forEach((element) => statObserver.observe(element));
}

function updateMiniGameUi() {
  if (miniGameScore) {
    miniGameScore.textContent = String(miniGameState.scrap);
  }

  if (miniGameHp) {
    miniGameHp.textContent = String(Math.max(0, Math.round(miniGameState.baseHp)));
  }

  if (miniGameTimer) {
    miniGameTimer.textContent = String(miniGameState.wave);
  }

  if (miniGameStartBtn) {
    miniGameStartBtn.disabled = miniGameState.running;
  }

  miniGameBuildTools.forEach((button) => {
    button.classList.toggle("is-active", button.dataset.buildTool === miniGameState.selectedTool);
  });
}

function resizeMiniGameCanvas() {
  if (!miniGameCanvas || !miniGameArena) {
    return;
  }

  const ratio = window.devicePixelRatio || 1;
  const rect = miniGameArena.getBoundingClientRect();
  const nextWidth = Math.max(Math.floor(rect.width), 320);
  const nextHeight = Math.max(Math.floor(rect.height), 300);

  miniGameCanvas.width = Math.floor(nextWidth * ratio);
  miniGameCanvas.height = Math.floor(nextHeight * ratio);
  miniGameCanvas.style.width = `${nextWidth}px`;
  miniGameCanvas.style.height = `${nextHeight}px`;

  syncMiniGameGrid();
}

function finishMiniGame() {
  miniGameState.running = false;
  miniGameState.waveActive = false;
  if (miniGameState.animationId) {
    window.cancelAnimationFrame(miniGameState.animationId);
    miniGameState.animationId = 0;
  }
  updateMiniGameUi();

  if (miniGameArena) {
    miniGameArena.classList.remove("is-live");
  }

  if (miniGameOverlayText) {
    miniGameOverlayText.textContent = `Base jebol di wave ${miniGameState.wave}. Total kill ${miniGameState.kills}.`;
  }

  setMiniGameStatus("Game over. Reset dulu kalau mau bangun strategi baru.");
  drawMiniGameScene();
}

function resetMiniGame() {
  if (miniGameState.animationId) {
    window.cancelAnimationFrame(miniGameState.animationId);
  }

  resizeMiniGameCanvas();

  const canvasWidth = miniGameCanvas?.clientWidth || 720;
  const canvasHeight = miniGameCanvas?.clientHeight || 400;
  miniGameState = {
    running: false,
    scrap: 120,
    baseHp: 100,
    wave: 1,
    kills: 0,
    animationId: 0,
    selectedTool: miniGameState.selectedTool || "turret",
    grid: { cols: 18, rows: 10, cellSize: 40, offsetX: 0, offsetY: 0 },
    turrets: [],
    walls: [],
    bullets: [],
    enemies: [],
    effects: [],
    pointer: { x: canvasWidth / 2, y: canvasHeight / 2, inside: false, col: -1, row: -1 },
    spawnQueue: 0,
    spawnCooldown: 0,
    waveActive: false,
    baseFlash: 0,
    screenShake: 0,
    wavePulse: 0,
    ambientCooldown: 0,
    lastFrameAt: 0
  };
  syncMiniGameGrid();

  if (miniGameArena) {
    miniGameArena.classList.remove("is-live");
  }

  if (miniGameOverlayText) {
    miniGameOverlayText.textContent = "Pilih tank atau tembok, klik grid buat bangun, lalu start wave.";
  }

  updateMiniGameUi();
  setMiniGameStatus("Modal awal 120 scrap. Tank 40, tembok 15, hapus bangunan buat refund kecil.");
  drawMiniGameScene();
}

function startMiniGame() {
  if (!miniGameArena || !miniGameCanvas || miniGameState.running) {
    return;
  }

  miniGameState.running = true;
  miniGameState.waveActive = true;
  miniGameState.spawnQueue = 14 + (miniGameState.wave * 7);
  miniGameState.spawnCooldown = 0;
  miniGameArena.classList.add("is-live");
  miniGameOverlayText.textContent = `Wave ${miniGameState.wave} masuk rame. Tank auto tembak, tembok paksa musuh muter.`;
  setMiniGameStatus("Wave jalan. Musuh nyebar dari beberapa lane, siapin choke point.");
  updateMiniGameUi();
  miniGameState.lastFrameAt = performance.now();
  miniGameState.animationId = window.requestAnimationFrame(runMiniGameFrame);
}

function setupMiniGame() {
  if (!miniGameArena || !miniGameCanvas || !miniGameStartBtn || !miniGameResetBtn) {
    return;
  }

  resetMiniGame();
  window.addEventListener("resize", () => {
    resizeMiniGameCanvas();
    drawMiniGameScene();
  });

  miniGameStartBtn.addEventListener("click", () => {
    startMiniGame();
  });

  miniGameResetBtn.addEventListener("click", () => {
    resetMiniGame();
  });

  miniGameBuildTools.forEach((button) => {
    button.addEventListener("click", () => {
      miniGameState.selectedTool = button.dataset.buildTool || "turret";
      updateMiniGameUi();
      setMiniGameStatus(`Mode ${getMiniGameToolLabel(miniGameState.selectedTool)} aktif. Klik grid buat eksekusi.`);
    });
  });

  window.addEventListener("keydown", (event) => {
    if (["INPUT", "TEXTAREA", "SELECT"].includes(document.activeElement?.tagName || "")) {
      return;
    }

    if (["1", "2", "3", " "].includes(event.key.toLowerCase())) {
      event.preventDefault();
    }

    if (event.key === "1") {
      miniGameState.selectedTool = "turret";
      updateMiniGameUi();
    } else if (event.key === "2") {
      miniGameState.selectedTool = "wall";
      updateMiniGameUi();
    } else if (event.key === "3") {
      miniGameState.selectedTool = "erase";
      updateMiniGameUi();
    } else if (event.key === " ") {
      startMiniGame();
      return;
    }
  });

  miniGameCanvas.addEventListener("pointermove", (event) => {
    updateMiniGamePointerFromEvent(event);
    drawMiniGameScene();
  });

  miniGameCanvas.addEventListener("pointerleave", () => {
    miniGameState.pointer.inside = false;
    miniGameState.pointer.col = -1;
    miniGameState.pointer.row = -1;
    drawMiniGameScene();
  });

  miniGameCanvas.addEventListener("click", (event) => {
    updateMiniGamePointerFromEvent(event);
    placeMiniGameBuilding();
  });

  miniGameCanvas.addEventListener("contextmenu", (event) => {
    event.preventDefault();
    updateMiniGamePointerFromEvent(event);
    eraseMiniGameBuilding();
  });
}

function getMiniGameToolLabel(tool) {
  if (tool === "wall") return "tembok";
  if (tool === "erase") return "hapus";
  return "tank";
}

function syncMiniGameGrid() {
  const width = miniGameCanvas?.clientWidth || 720;
  const height = miniGameCanvas?.clientHeight || 400;
  const cols = 18;
  const rows = 10;
  const cellSize = Math.floor(Math.min(width / cols, height / rows));
  miniGameState.grid = {
    cols,
    rows,
    cellSize,
    offsetX: Math.floor((width - (cols * cellSize)) / 2),
    offsetY: Math.floor((height - (rows * cellSize)) / 2)
  };
  updateMiniGamePointerCell();
}

function updateMiniGamePointerCell() {
  const { cellSize, offsetX, offsetY, cols, rows } = miniGameState.grid;
  const col = Math.floor((miniGameState.pointer.x - offsetX) / cellSize);
  const row = Math.floor((miniGameState.pointer.y - offsetY) / cellSize);
  miniGameState.pointer.col = col >= 0 && col < cols ? col : -1;
  miniGameState.pointer.row = row >= 0 && row < rows ? row : -1;
}

function updateMiniGamePointerFromEvent(event) {
  if (!miniGameCanvas) {
    return;
  }

  const rect = miniGameCanvas.getBoundingClientRect();
  miniGameState.pointer.x = event.clientX - rect.left;
  miniGameState.pointer.y = event.clientY - rect.top;
  miniGameState.pointer.inside = true;
  updateMiniGamePointerCell();
}

function getMiniGameCellCenter(col, row) {
  const { cellSize, offsetX, offsetY } = miniGameState.grid;
  return {
    x: offsetX + (col * cellSize) + (cellSize / 2),
    y: offsetY + (row * cellSize) + (cellSize / 2)
  };
}

function getMiniGameCellKey(col, row) {
  return `${col}:${row}`;
}

function getMiniGameSpawnCell() {
  return { col: 0, row: Math.floor(miniGameState.grid.rows / 2) };
}

function getMiniGameSpawnRows() {
  return [1, 2, 4, 5, 7, 8].filter((row) => row < miniGameState.grid.rows);
}

function getMiniGameBaseCell() {
  return { col: miniGameState.grid.cols - 1, row: Math.floor(miniGameState.grid.rows / 2) };
}

function isMiniGameReservedCell(col, row) {
  const base = getMiniGameBaseCell();
  return (col === 0 && getMiniGameSpawnRows().includes(row)) || (col === base.col && Math.abs(row - base.row) <= 1);
}

function getMiniGameWallAt(col, row) {
  return miniGameState.walls.find((wall) => wall.col === col && wall.row === row);
}

function getMiniGameTurretAt(col, row) {
  return miniGameState.turrets.find((turret) => turret.col === col && turret.row === row);
}

function addMiniGameEffect(effect) {
  miniGameState.effects.push({
    age: 0,
    duration: 0.45,
    ...effect
  });
}

function drawMiniGameRoundRect(context, x, y, width, height, radius) {
  const nextRadius = Math.min(radius, width / 2, height / 2);
  context.beginPath();
  context.moveTo(x + nextRadius, y);
  context.lineTo(x + width - nextRadius, y);
  context.quadraticCurveTo(x + width, y, x + width, y + nextRadius);
  context.lineTo(x + width, y + height - nextRadius);
  context.quadraticCurveTo(x + width, y + height, x + width - nextRadius, y + height);
  context.lineTo(x + nextRadius, y + height);
  context.quadraticCurveTo(x, y + height, x, y + height - nextRadius);
  context.lineTo(x, y + nextRadius);
  context.quadraticCurveTo(x, y, x + nextRadius, y);
  context.closePath();
}

function canMiniGamePathReachBase(walls = miniGameState.walls) {
  const spawn = getMiniGameSpawnCell();
  const base = getMiniGameBaseCell();
  const blocked = new Set(walls.map((wall) => getMiniGameCellKey(wall.col, wall.row)));
  const queue = [spawn];
  const visited = new Set([getMiniGameCellKey(spawn.col, spawn.row)]);

  for (let index = 0; index < queue.length; index += 1) {
    const cell = queue[index];
    if (cell.col === base.col && cell.row === base.row) {
      return true;
    }

    [[1, 0], [-1, 0], [0, 1], [0, -1]].forEach(([dc, dr]) => {
      const col = cell.col + dc;
      const row = cell.row + dr;
      const key = getMiniGameCellKey(col, row);
      if (col < 0 || row < 0 || col >= miniGameState.grid.cols || row >= miniGameState.grid.rows || visited.has(key) || blocked.has(key)) {
        return;
      }
      visited.add(key);
      queue.push({ col, row });
    });
  }

  return false;
}

function placeMiniGameBuilding() {
  const { col, row } = miniGameState.pointer;
  if (col < 0 || row < 0) {
    return;
  }

  const existingWall = getMiniGameWallAt(col, row);
  const existingTurret = getMiniGameTurretAt(col, row);

  if (miniGameState.selectedTool === "erase") {
    eraseMiniGameBuilding();
    return;
  }

  if (isMiniGameReservedCell(col, row)) {
    setMiniGameStatus("Spawn dan base jangan ditutup. Musuh harus punya jalur masuk.");
    return;
  }

  if (existingWall && miniGameState.selectedTool === "turret") {
    replaceMiniGameWallWithTurret(existingWall);
    return;
  }

  if (existingTurret && miniGameState.selectedTool === "wall") {
    replaceMiniGameTurretWithWall(existingTurret);
    return;
  }

  if (existingWall || existingTurret) {
    setMiniGameStatus("Kotak itu sudah kepakai. Pakai mode Hapus, klik kanan, atau pilih tool lain buat ganti.");
    return;
  }

  if (miniGameState.selectedTool === "wall") {
    if (miniGameState.scrap < 15) {
      setMiniGameStatus("Scrap kurang buat tembok.");
      return;
    }

    const nextWalls = [...miniGameState.walls, { col, row, hp: 70 }];
    if (!canMiniGamePathReachBase(nextWalls)) {
      setMiniGameStatus("Tembok itu nge-lock jalan total. Bikin maze boleh, nutup full jangan.");
      return;
    }

    miniGameState.walls = nextWalls;
    miniGameState.scrap -= 15;
    const center = getMiniGameCellCenter(col, row);
    addMiniGameEffect({ type: "build", x: center.x, y: center.y, color: "rgba(131, 157, 189, 0.9)", duration: 0.42 });
    setMiniGameStatus("Tembok jadi. Musuh bakal dipaksa muter.");
  } else {
    if (miniGameState.scrap < 40) {
      setMiniGameStatus("Scrap kurang buat tank.");
      return;
    }

    miniGameState.turrets.push({ col, row, cooldown: 0, range: 128 });
    miniGameState.scrap -= 40;
    const center = getMiniGameCellCenter(col, row);
    addMiniGameEffect({ type: "build", x: center.x, y: center.y, color: "rgba(153, 223, 255, 0.95)", duration: 0.55 });
    setMiniGameStatus("Tank online. Meriam auto-lock musuh paling dekat.");
  }

  updateMiniGameUi();
  drawMiniGameScene();
}

function eraseMiniGameBuilding() {
  const { col, row } = miniGameState.pointer;
  const existingWall = getMiniGameWallAt(col, row);
  const existingTurret = getMiniGameTurretAt(col, row);

  if (existingWall) {
    miniGameState.walls = miniGameState.walls.filter((wall) => wall !== existingWall);
    miniGameState.scrap += 6;
    setMiniGameStatus("Tembok dibongkar. Scrap balik dikit, ekonomi tetap harus hemat.");
  } else if (existingTurret) {
    miniGameState.turrets = miniGameState.turrets.filter((turret) => turret !== existingTurret);
    miniGameState.scrap += 18;
    setMiniGameStatus("Tank dijual. Posisi bisa diatur ulang.");
  } else {
    setMiniGameStatus("Kotak ini kosong, mon.");
  }

  updateMiniGameUi();
  drawMiniGameScene();
}

function replaceMiniGameWallWithTurret(wall) {
  const upgradeCost = 25;
  if (miniGameState.scrap < upgradeCost) {
    setMiniGameStatus("Scrap kurang buat ganti tembok jadi tank. Butuh 25 scrap.");
    return;
  }

  miniGameState.walls = miniGameState.walls.filter((item) => item !== wall);
  miniGameState.turrets.push({ col: wall.col, row: wall.row, cooldown: 0, range: 128 });
  miniGameState.scrap -= upgradeCost;
  const center = getMiniGameCellCenter(wall.col, wall.row);
  addMiniGameEffect({ type: "build", x: center.x, y: center.y, color: "rgba(153, 223, 255, 0.95)", duration: 0.55 });
  setMiniGameStatus("Tembok diganti jadi tank. Layout kebenerin, gas tahan wave.");
  updateMiniGameUi();
  drawMiniGameScene();
}

function replaceMiniGameTurretWithWall(turret) {
  const nextWalls = [...miniGameState.walls, { col: turret.col, row: turret.row, hp: 70 }];
  if (!canMiniGamePathReachBase(nextWalls)) {
    setMiniGameStatus("Ganti tank jadi tembok di sini bakal nutup jalan total.");
    return;
  }

  miniGameState.turrets = miniGameState.turrets.filter((item) => item !== turret);
  miniGameState.walls = nextWalls;
  miniGameState.scrap += 3;
  const center = getMiniGameCellCenter(turret.col, turret.row);
  addMiniGameEffect({ type: "build", x: center.x, y: center.y, color: "rgba(131, 157, 189, 0.9)", duration: 0.42 });
  setMiniGameStatus("Tank diganti jadi tembok. Refund kecil masuk.");
  updateMiniGameUi();
  drawMiniGameScene();
}

function spawnMiniGameEnemy() {
  const laneRows = getMiniGameSpawnRows();
  const row = laneRows[Math.floor(Math.random() * laneRows.length)] ?? getMiniGameSpawnCell().row;
  const center = getMiniGameCellCenter(0, row);
  const waveScale = Math.max(0, miniGameState.wave - 1);
  const isRunner = Math.random() < 0.28;
  const maxHp = isRunner ? 24 + (waveScale * 6) : 38 + (waveScale * 9);

  miniGameState.enemies.push({
    x: center.x - miniGameState.grid.cellSize - (Math.random() * miniGameState.grid.cellSize * 2.5),
    y: center.y + ((Math.random() - 0.5) * miniGameState.grid.cellSize * 0.55),
    col: 0,
    row,
    radius: Math.max(10, miniGameState.grid.cellSize * (isRunner ? 0.24 : 0.3)),
    hp: maxHp,
    maxHp,
    speed: (isRunner ? 72 : 52) + (waveScale * 5) + (Math.random() * 10),
    type: isRunner ? "runner" : "bruiser",
    path: [],
    pathIndex: 0
  });

  addMiniGameEffect({
    type: "spawn",
    x: center.x,
    y: center.y,
    row,
    duration: 0.55
  });
}

function drawMiniGameScene() {
  if (!miniGameCanvas) {
    return;
  }

  const context = miniGameCanvas.getContext("2d");
  if (!context) {
    return;
  }

  const ratio = window.devicePixelRatio || 1;
  const width = miniGameCanvas.width / ratio;
  const height = miniGameCanvas.height / ratio;
  context.setTransform(ratio, 0, 0, ratio, 0, 0);
  context.clearRect(0, 0, width, height);

  const now = performance.now() / 1000;
  const shake = miniGameState.screenShake || 0;
  const shakeX = shake ? Math.sin(now * 96) * shake * 5 : 0;
  const shakeY = shake ? Math.cos(now * 84) * shake * 4 : 0;
  context.save();
  context.translate(shakeX, shakeY);

  context.fillStyle = "rgba(5, 12, 22, 0.72)";
  context.fillRect(0, 0, width, height);

  const { cols, rows, cellSize, offsetX, offsetY } = miniGameState.grid;
  const boardWidth = cols * cellSize;
  const boardHeight = rows * cellSize;

  context.fillStyle = "rgba(8, 19, 34, 0.82)";
  context.fillRect(offsetX, offsetY, boardWidth, boardHeight);

  context.strokeStyle = "rgba(255, 255, 255, 0.08)";
  context.lineWidth = 1;
  for (let col = 0; col <= cols; col += 1) {
    const x = offsetX + (col * cellSize);
    context.beginPath();
    context.moveTo(x, offsetY);
    context.lineTo(x, offsetY + boardHeight);
    context.stroke();
  }
  for (let row = 0; row <= rows; row += 1) {
    const y = offsetY + (row * cellSize);
    context.beginPath();
    context.moveTo(offsetX, y);
    context.lineTo(offsetX + boardWidth, y);
    context.stroke();
  }

  const base = getMiniGameBaseCell();
  const baseCenter = getMiniGameCellCenter(base.col, base.row);
  const spawnRows = getMiniGameSpawnRows();

  context.fillStyle = "rgba(255, 92, 92, 0.22)";
  spawnRows.forEach((row) => {
    context.fillRect(offsetX, offsetY + (row * cellSize), cellSize, cellSize);
  });
  context.fillStyle = "rgba(236, 230, 31, 0.18)";
  context.fillRect(baseCenter.x - (cellSize / 2), baseCenter.y - (cellSize * 1.5), cellSize, cellSize * 3);
  if (miniGameState.baseFlash > 0) {
    context.fillStyle = `rgba(255, 92, 92, ${0.28 * miniGameState.baseFlash})`;
    context.fillRect(baseCenter.x - (cellSize / 2), baseCenter.y - (cellSize * 1.5), cellSize, cellSize * 3);
  }

  context.fillStyle = "#ff7878";
  context.font = `700 ${Math.max(11, cellSize * 0.28)}px Rajdhani, sans-serif`;
  context.textAlign = "center";
  context.fillText("LANE", offsetX + (cellSize / 2), offsetY + (cellSize * 0.65));
  context.fillStyle = "#ece61f";
  context.fillText("BASE", baseCenter.x, baseCenter.y + 4);

  miniGameState.effects.forEach((effect) => {
    const progress = Math.min(effect.age / effect.duration, 1);
    const alpha = 1 - progress;

    if (effect.type === "spawn") {
      context.fillStyle = `rgba(255, 92, 92, ${0.28 * alpha})`;
      context.fillRect(offsetX, offsetY + (effect.row * cellSize), cellSize * (1.2 + progress * 2.8), cellSize);
      context.strokeStyle = `rgba(255, 180, 92, ${0.82 * alpha})`;
      context.lineWidth = 2;
      context.beginPath();
      context.arc(effect.x, effect.y, cellSize * (0.35 + progress * 0.85), 0, Math.PI * 2);
      context.stroke();
    } else if (effect.type === "spark") {
      context.strokeStyle = `rgba(255, 233, 122, ${0.9 * alpha})`;
      context.lineWidth = 2;
      for (let index = 0; index < 5; index += 1) {
        const angle = effect.angle + index * 1.26;
        const inner = effect.radius * progress * 0.2;
        const outer = effect.radius * (0.35 + progress);
        context.beginPath();
        context.moveTo(effect.x + Math.cos(angle) * inner, effect.y + Math.sin(angle) * inner);
        context.lineTo(effect.x + Math.cos(angle) * outer, effect.y + Math.sin(angle) * outer);
        context.stroke();
      }
    } else if (effect.type === "wave") {
      context.strokeStyle = `rgba(236, 230, 31, ${0.72 * alpha})`;
      context.lineWidth = 3;
      context.beginPath();
      context.arc(baseCenter.x, baseCenter.y, cellSize * (1 + progress * 7), 0, Math.PI * 2);
      context.stroke();
    } else if (effect.type === "build") {
      context.strokeStyle = effect.color || `rgba(153, 223, 255, ${alpha})`;
      context.lineWidth = 3;
      context.beginPath();
      context.arc(effect.x, effect.y, cellSize * (0.24 + progress * 1.25), 0, Math.PI * 2);
      context.stroke();
      context.fillStyle = `rgba(255, 255, 255, ${0.12 * alpha})`;
      context.fillRect(effect.x - (cellSize * 0.42), effect.y - (cellSize * 0.42), cellSize * 0.84, cellSize * 0.84);
    } else if (effect.type === "ambient") {
      context.fillStyle = `rgba(153, 223, 255, ${0.44 * alpha})`;
      context.beginPath();
      context.arc(effect.x, effect.y, 2 + progress * 9, 0, Math.PI * 2);
      context.fill();
    }
  });

  miniGameState.walls.forEach((wall) => {
    const center = getMiniGameCellCenter(wall.col, wall.row);
    const wallPulse = 0.5 + Math.sin(now * 3.2 + wall.col * 0.7 + wall.row) * 0.5;
    context.fillStyle = "rgba(131, 157, 189, 0.86)";
    context.fillRect(center.x - (cellSize * 0.38), center.y - (cellSize * 0.38), cellSize * 0.76, cellSize * 0.76);
    context.strokeStyle = `rgba(255, 255, 255, ${0.18 + wallPulse * 0.18})`;
    context.lineWidth = 2;
    context.strokeRect(center.x - (cellSize * 0.38), center.y - (cellSize * 0.38), cellSize * 0.76, cellSize * 0.76);
  });

  miniGameState.turrets.forEach((turret) => {
    const center = getMiniGameCellCenter(turret.col, turret.row);
    const idlePulse = 0.5 + (Math.sin(now * 4 + turret.col + turret.row) * 0.5);
    context.fillStyle = `rgba(153, 223, 255, ${0.1 + idlePulse * 0.08})`;
    context.beginPath();
    context.arc(center.x, center.y, turret.range, 0, Math.PI * 2);
    context.fill();

    const target = miniGameState.enemies
      .filter((enemy) => Math.hypot(enemy.x - center.x, enemy.y - center.y) <= turret.range)
      .sort((a, b) => Math.hypot(a.x - center.x, a.y - center.y) - Math.hypot(b.x - center.x, b.y - center.y))[0];
    const aimAngle = target ? Math.atan2(target.y - center.y, target.x - center.x) : Math.PI;

    context.save();
    context.translate(center.x, center.y);
    context.rotate(aimAngle);
    const recoil = turret.recoil ? turret.recoil * cellSize * 0.12 : 0;
    context.translate(-recoil, 0);

    const trackWidth = cellSize * 0.2;
    const tankLength = cellSize * 0.82;
    const tankHeight = cellSize * 0.66;
    const hullLength = cellSize * 0.54;
    const hullHeight = cellSize * 0.48;

    context.fillStyle = "rgba(0, 0, 0, 0.34)";
    drawMiniGameRoundRect(context, -tankLength * 0.5, -tankHeight * 0.5, tankLength, tankHeight, cellSize * 0.12);
    context.fill();

    context.fillStyle = "#23313a";
    drawMiniGameRoundRect(context, -tankLength * 0.48, -tankHeight * 0.5, tankLength, trackWidth, cellSize * 0.08);
    context.fill();
    drawMiniGameRoundRect(context, -tankLength * 0.48, tankHeight * 0.5 - trackWidth, tankLength, trackWidth, cellSize * 0.08);
    context.fill();

    context.strokeStyle = "rgba(255, 255, 255, 0.18)";
    context.lineWidth = 1.5;
    for (let tread = -0.28; tread <= 0.28; tread += 0.14) {
      context.beginPath();
      context.moveTo(tread * cellSize, -tankHeight * 0.48);
      context.lineTo((tread + 0.06) * cellSize, -tankHeight * 0.5 + trackWidth);
      context.moveTo(tread * cellSize, tankHeight * 0.48);
      context.lineTo((tread + 0.06) * cellSize, tankHeight * 0.5 - trackWidth);
      context.stroke();
    }

    context.fillStyle = "#6fd2ee";
    drawMiniGameRoundRect(context, -hullLength * 0.5, -hullHeight * 0.5, hullLength, hullHeight, cellSize * 0.1);
    context.fill();

    context.fillStyle = "#b8f4ff";
    context.beginPath();
    context.arc(cellSize * 0.02, 0, cellSize * 0.18, 0, Math.PI * 2);
    context.fill();

    context.fillStyle = "#e7fbff";
    drawMiniGameRoundRect(context, cellSize * 0.08, -cellSize * 0.055, cellSize * 0.5, cellSize * 0.11, cellSize * 0.035);
    context.fill();

    context.fillStyle = "#ffffff";
    drawMiniGameRoundRect(context, cellSize * 0.48, -cellSize * 0.04, cellSize * 0.13, cellSize * 0.08, cellSize * 0.02);
    context.fill();

    if (turret.recoil > 0.04) {
      context.fillStyle = `rgba(255, 233, 122, ${turret.recoil})`;
      context.beginPath();
      context.moveTo(cellSize * 0.6, 0);
      context.lineTo(cellSize * 0.86, -cellSize * 0.13);
      context.lineTo(cellSize * 0.86, cellSize * 0.13);
      context.closePath();
      context.fill();
    }

    context.strokeStyle = "rgba(236, 230, 31, 0.72)";
    context.lineWidth = 2;
    drawMiniGameRoundRect(context, -hullLength * 0.5, -hullHeight * 0.5, hullLength, hullHeight, cellSize * 0.1);
    context.stroke();

    context.restore();
  });

  miniGameState.bullets.forEach((bullet) => {
    context.strokeStyle = "rgba(255, 233, 122, 0.42)";
    context.lineWidth = 3;
    context.beginPath();
    context.moveTo(bullet.x, bullet.y);
    context.lineTo(bullet.prevX || bullet.x, bullet.prevY || bullet.y);
    context.stroke();
    context.fillStyle = "#ffe97a";
    context.beginPath();
    context.arc(bullet.x, bullet.y, bullet.radius, 0, Math.PI * 2);
    context.fill();
  });

  miniGameState.enemies.forEach((enemy) => {
    const hitGlow = enemy.hitFlash || 0;
    context.strokeStyle = enemy.type === "runner" ? "rgba(255, 180, 92, 0.24)" : "rgba(255, 92, 92, 0.2)";
    context.lineWidth = enemy.radius * 0.45;
    context.beginPath();
    context.moveTo(enemy.x - enemy.radius * 1.5, enemy.y);
    context.lineTo(enemy.x - enemy.radius * 3.2, enemy.y);
    context.stroke();

    context.fillStyle = hitGlow > 0.05 ? "#fff2a8" : (enemy.type === "runner" ? "#ffb45c" : "#ff5c5c");
    context.beginPath();
    context.arc(enemy.x, enemy.y, enemy.radius, 0, Math.PI * 2);
    context.fill();

    context.fillStyle = "rgba(8, 19, 34, 0.65)";
    context.beginPath();
    context.arc(enemy.x + enemy.radius * 0.24, enemy.y - enemy.radius * 0.18, enemy.radius * 0.24, 0, Math.PI * 2);
    context.fill();

    context.strokeStyle = "rgba(255, 255, 255, 0.12)";
    context.lineWidth = 2;
    context.beginPath();
    context.arc(enemy.x, enemy.y, enemy.radius + 6, 0, Math.PI * 2);
    context.stroke();

    context.fillStyle = "rgba(0, 0, 0, 0.48)";
    context.fillRect(enemy.x - 16, enemy.y - enemy.radius - 12, 32, 4);
    context.fillStyle = "#ece61f";
    context.fillRect(enemy.x - 16, enemy.y - enemy.radius - 12, 32 * Math.max(0, enemy.hp / enemy.maxHp), 4);
  });

  if (miniGameState.pointer.inside && miniGameState.pointer.col >= 0 && miniGameState.pointer.row >= 0) {
    const center = getMiniGameCellCenter(miniGameState.pointer.col, miniGameState.pointer.row);
    context.strokeStyle = miniGameState.selectedTool === "erase" ? "rgba(255, 92, 92, 0.9)" : "rgba(153, 223, 255, 0.9)";
    context.lineWidth = 3;
    context.strokeRect(center.x - (cellSize / 2) + 3, center.y - (cellSize / 2) + 3, cellSize - 6, cellSize - 6);
  }

  context.restore();
}

function findMiniGamePath(startCol, startRow) {
  const base = getMiniGameBaseCell();
  const blocked = new Set(miniGameState.walls.map((wall) => getMiniGameCellKey(wall.col, wall.row)));
  const startKey = getMiniGameCellKey(startCol, startRow);
  const queue = [{ col: startCol, row: startRow }];
  const cameFrom = new Map([[startKey, null]]);

  for (let index = 0; index < queue.length; index += 1) {
    const cell = queue[index];
    if (cell.col === base.col && cell.row === base.row) {
      const path = [];
      let key = getMiniGameCellKey(cell.col, cell.row);
      while (key) {
        const [col, row] = key.split(":").map(Number);
        path.unshift({ col, row });
        key = cameFrom.get(key);
      }
      return path;
    }

    [[1, 0], [0, -1], [0, 1], [-1, 0]].forEach(([dc, dr]) => {
      const col = cell.col + dc;
      const row = cell.row + dr;
      const key = getMiniGameCellKey(col, row);
      if (col < 0 || row < 0 || col >= miniGameState.grid.cols || row >= miniGameState.grid.rows || cameFrom.has(key) || blocked.has(key)) {
        return;
      }
      cameFrom.set(key, getMiniGameCellKey(cell.col, cell.row));
      queue.push({ col, row });
    });
  }

  return [{ col: startCol, row: startRow }, base];
}

function runMiniGameFrame(now) {
  if (!miniGameState.running || !miniGameCanvas) {
    return;
  }

  const delta = Math.min((now - miniGameState.lastFrameAt) / 1000, 0.032);
  miniGameState.lastFrameAt = now;

  miniGameState.baseFlash = Math.max(0, miniGameState.baseFlash - (delta * 2.6));
  miniGameState.screenShake = Math.max(0, miniGameState.screenShake - (delta * 3.4));
  miniGameState.wavePulse = Math.max(0, miniGameState.wavePulse - delta);
  miniGameState.effects = miniGameState.effects
    .map((effect) => ({ ...effect, age: effect.age + delta }))
    .filter((effect) => effect.age < effect.duration);
  miniGameState.ambientCooldown -= delta;
  if (miniGameState.running && miniGameState.ambientCooldown <= 0) {
    miniGameState.ambientCooldown = 0.18 + Math.random() * 0.28;
    addMiniGameEffect({
      type: "ambient",
      x: miniGameState.grid.offsetX + Math.random() * miniGameState.grid.cols * miniGameState.grid.cellSize,
      y: miniGameState.grid.offsetY + Math.random() * miniGameState.grid.rows * miniGameState.grid.cellSize,
      duration: 0.7
    });
  }
  miniGameState.spawnCooldown -= delta;

  if (miniGameState.spawnQueue > 0 && miniGameState.spawnCooldown <= 0) {
    spawnMiniGameEnemy();
    miniGameState.spawnQueue -= 1;
    miniGameState.spawnCooldown = Math.max(0.16, 0.46 - (miniGameState.wave * 0.025));
  }

  miniGameState.turrets.forEach((turret) => {
    turret.cooldown = Math.max(0, turret.cooldown - delta);
    turret.recoil = Math.max(0, (turret.recoil || 0) - (delta * 5));
    if (turret.cooldown > 0) {
      return;
    }

    const center = getMiniGameCellCenter(turret.col, turret.row);
    const target = miniGameState.enemies
      .filter((enemy) => Math.hypot(enemy.x - center.x, enemy.y - center.y) <= turret.range)
      .sort((a, b) => Math.hypot(a.x - center.x, a.y - center.y) - Math.hypot(b.x - center.x, b.y - center.y))[0];

    if (!target) {
      return;
    }

    miniGameState.bullets.push({
      x: center.x,
      y: center.y,
      prevX: center.x,
      prevY: center.y,
      radius: 4,
      target,
      speed: 360,
      damage: 18 + Math.min(12, miniGameState.wave)
    });
    turret.recoil = 1;
    turret.cooldown = 0.72;
  });

  miniGameState.bullets = miniGameState.bullets.filter((bullet) => {
    if (!miniGameState.enemies.includes(bullet.target)) {
      return false;
    }

    const angle = Math.atan2(bullet.target.y - bullet.y, bullet.target.x - bullet.x);
    bullet.prevX = bullet.x;
    bullet.prevY = bullet.y;
    bullet.x += Math.cos(angle) * bullet.speed * delta;
    bullet.y += Math.sin(angle) * bullet.speed * delta;

    if (Math.hypot(bullet.target.x - bullet.x, bullet.target.y - bullet.y) < bullet.target.radius + 4) {
      bullet.target.hp -= bullet.damage;
      bullet.target.hitFlash = 1;
      addMiniGameEffect({
        type: "spark",
        x: bullet.target.x,
        y: bullet.target.y,
        angle,
        radius: 22,
        duration: 0.28
      });
      return false;
    }

    return true;
  });

  const nextEnemies = [];
  miniGameState.enemies.forEach((enemy) => {
    enemy.hitFlash = Math.max(0, (enemy.hitFlash || 0) - (delta * 5));

    if (enemy.hp <= 0) {
      miniGameState.kills += 1;
      miniGameState.scrap += 12;
      addMiniGameEffect({
        type: "spark",
        x: enemy.x,
        y: enemy.y,
        angle: Math.random() * Math.PI * 2,
        radius: 34,
        duration: 0.42
      });
      setMiniGameStatus("Bot tumbang. Scrap naik, bisa upgrade layout.");
      return;
    }

    enemy.col = Math.min(miniGameState.grid.cols - 1, Math.max(0, Math.floor((enemy.x - miniGameState.grid.offsetX) / miniGameState.grid.cellSize)));
    enemy.row = Math.min(miniGameState.grid.rows - 1, Math.max(0, Math.floor((enemy.y - miniGameState.grid.offsetY) / miniGameState.grid.cellSize)));
    enemy.path = findMiniGamePath(enemy.col, enemy.row);

    const targetCell = enemy.path[1] || enemy.path[0] || getMiniGameBaseCell();
    const targetCenter = getMiniGameCellCenter(targetCell.col, targetCell.row);
    const angle = Math.atan2(targetCenter.y - enemy.y, targetCenter.x - enemy.x);
    enemy.x += Math.cos(angle) * enemy.speed * delta;
    enemy.y += Math.sin(angle) * enemy.speed * delta;

    const base = getMiniGameBaseCell();
    if (enemy.col === base.col && Math.abs(enemy.row - base.row) <= 1) {
      miniGameState.baseHp -= 10;
      miniGameState.baseFlash = 1;
      miniGameState.screenShake = 1;
      setMiniGameStatus("Base kena hit. Perkuat maze atau tambah tank.");
      return;
    }

    nextEnemies.push(enemy);
  });
  miniGameState.enemies = nextEnemies;

  updateMiniGameUi();
  drawMiniGameScene();

  if (miniGameState.baseHp <= 0) {
    finishMiniGame();
    return;
  }

  if (miniGameState.spawnQueue <= 0 && miniGameState.enemies.length === 0) {
    miniGameState.running = false;
    miniGameState.waveActive = false;
    miniGameState.wave += 1;
    miniGameState.scrap += 30;
    miniGameState.wavePulse = 0.8;
    addMiniGameEffect({
      type: "wave",
      x: 0,
      y: 0,
      duration: 0.8
    });
    miniGameArena.classList.remove("is-live");
    if (miniGameOverlayText) {
      miniGameOverlayText.textContent = `Wave clear. Dapat bonus 30 scrap. Siapin defense buat wave ${miniGameState.wave}.`;
    }
    setMiniGameStatus("Wave clear. Bangun lagi lalu start wave berikutnya.");
    updateMiniGameUi();
    drawMiniGameScene();
    return;
  }

  miniGameState.animationId = window.requestAnimationFrame(runMiniGameFrame);
}

if (specialButton) {
  specialButton.addEventListener("click", () => {
    const roll = specials[Math.floor(Math.random() * specials.length)];
    specialButton.textContent = roll;
    specialButton.classList.remove("spin-once");
    void specialButton.offsetWidth;
    specialButton.classList.add("spin-once");
    pulseElement(heroCard);
  });
}

if (quickAddButton && quickMenu) {
  quickAddButton.addEventListener("click", () => {
    addToCart(quickMenu.value);
  });
}

if (form) {
  form.addEventListener("submit", (event) => {
    event.preventDefault();
    updateDeliveryLinks();
    openWhatsAppOrder(buildOrderMessage());
    setStatusMessage("Order dibuka ke WhatsApp warung. Tinggal kirim pesannya.");
  });
}

if (customerName || orderNote) {
  [customerName, orderNote].forEach((field) => {
    field?.addEventListener("input", updateDeliveryLinks);
  });
}

if (musicToggle) {
  updateMusicButton();
  if (bgMusic) {
    bgMusic.volume = 0.85;
    bgMusic.muted = false;
    bgMusic.defaultMuted = false;
    bgMusic.load();
    updateVolumeVisual();
    updateMusicProgress();
  }

  musicToggle.addEventListener("click", async () => {
    if (!bgMusic) {
      return;
    }

    if (isMusicPlaying) {
      bgMusic.pause();
      isMusicPlaying = false;
      stopBassTracking();
    } else {
      try {
        await bgMusic.play();
        isMusicPlaying = true;
        startSafeMusicVisuals();
      } catch (error) {
        isMusicPlaying = false;
        setStatusMessage("Musik belum mau nyala. Klik tombol sekali lagi.");
      }
    }

    updateMusicButton();
  });
}

if (bgMusic) {
  setBassVisuals(0);
  updateMusicProgress();
  updateVolumeVisual();

  bgMusic.addEventListener("play", () => {
    isMusicPlaying = true;
    startSafeMusicVisuals();
    updateMusicButton();
    updateMusicProgress();
  });

  bgMusic.addEventListener("pause", () => {
    isMusicPlaying = false;
    updateMusicButton();
    stopBassTracking();
  });

  bgMusic.addEventListener("ended", stopBassTracking);
  bgMusic.addEventListener("ended", () => {
    isMusicPlaying = false;
    updateMusicButton();
    updateMusicProgress();
  });
  bgMusic.addEventListener("loadedmetadata", updateMusicProgress);
  bgMusic.addEventListener("timeupdate", updateMusicProgress);
  bgMusic.addEventListener("volumechange", updateVolumeVisual);

  const tryAutoplayMusic = async () => {
    if (autoplayAttempted) {
      return;
    }

    autoplayAttempted = true;

    try {
      await bgMusic.play();
      isMusicPlaying = true;
      startSafeMusicVisuals();
    } catch (error) {
      isMusicPlaying = false;
    }

    updateMusicButton();
  };

  if (document.readyState === "complete") {
    tryAutoplayMusic();
  } else {
    window.addEventListener("load", tryAutoplayMusic, { once: true });
  }

  const unlockMusicOnFirstInteraction = async () => {
    if (isMusicPlaying) {
      return;
    }

    try {
      await bgMusic.play();
      isMusicPlaying = true;
      startSafeMusicVisuals();
      updateMusicButton();
    } catch (error) {
      isMusicPlaying = false;
    }
  };

  window.addEventListener("pointerdown", unlockMusicOnFirstInteraction, { once: true });
  window.addEventListener("keydown", unlockMusicOnFirstInteraction, { once: true });
}

if (musicVolume && bgMusic) {
  musicVolume.addEventListener("input", () => {
    bgMusic.volume = Number(musicVolume.value) / 100;
    updateVolumeVisual();
  });
}

if (musicProgress && bgMusic) {
  musicProgress.addEventListener("click", (event) => {
    const rect = musicProgress.getBoundingClientRect();
    const clickRatio = Math.min(Math.max((event.clientX - rect.left) / rect.width, 0), 1);

    if (Number.isFinite(bgMusic.duration) && bgMusic.duration > 0) {
      bgMusic.currentTime = bgMusic.duration * clickRatio;
      updateMusicProgress();
    }
  });
}

enablePanelSpotlight(cartPanel);

setupWallpaperRotator();
setupScrollProgress();
setupAmbientSpotlights();
setupSectionAnimations();
setupStatCounters();
setupMagneticButtons();
setupCursorEffects();
setupHeroParallax();
setupBreakingNewsCarousel();
setupFoodSlider();
setupMiniGame();
setupMenuRealtimeSync();
refreshMenuState();
window.setInterval(() => refreshMenuState(true), 5000);
