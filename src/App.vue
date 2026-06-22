<script setup>
import { computed, onMounted, onUnmounted, ref } from "vue";

const isMenuOpen = ref(false);
const isScrolled = ref(false);
const isReserved = ref(false);

const navItems = [
  { label: "菜单", href: "#menu" },
  { label: "主厨", href: "#story" },
  { label: "空间", href: "#space" },
  { label: "预订", href: "#reserve" },
];

const dishes = [
  {
    number: "01",
    title: "炭烤和牛",
    description: "黑蒜汁、烤甜葱、烟熏海盐。",
    image: "https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&w=900&q=80",
    alt: "香煎主菜配蔬菜",
  },
  {
    number: "02",
    title: "春田蔬菜盘",
    description: "发酵柠檬、榛子油、手作乳清酱。",
    image: "https://images.unsplash.com/photo-1512621776951-a57141f2eefd?auto=format&fit=crop&w=900&q=80",
    alt: "新鲜蔬菜沙拉",
  },
  {
    number: "03",
    title: "海盐烤季节鱼",
    description: "茴香、白葡萄酒汁、炭烤柑橘。",
    image: "https://images.unsplash.com/photo-1559847844-5315695dadae?auto=format&fit=crop&w=900&q=80",
    alt: "烤鱼与配菜",
  },
];

const stats = [
  { value: "46", label: "晚餐座位" },
  { value: "12", label: "季节酒款" },
  { value: "4", label: "开放厨房席" },
];

const spaceImages = [
  {
    src: "https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&w=1200&q=80",
    alt: "温暖灯光下的餐厅空间",
  },
  {
    src: "https://images.unsplash.com/photo-1555396273-367ea4eb4db5?auto=format&fit=crop&w=1000&q=80",
    alt: "餐厅吧台与座位",
  },
];

const partyOptions = ["2 位", "3 位", "4 位", "5-6 位"];

const navToggleLabel = computed(() => (isMenuOpen.value ? "关闭菜单" : "打开菜单"));
const submitText = computed(() => (isReserved.value ? "已收到预约" : "提交预订"));

const updateHeader = () => {
  isScrolled.value = window.scrollY > 24;
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = () => {
  isMenuOpen.value = false;
};

const submitReserve = () => {
  isReserved.value = true;
};

onMounted(() => {
  updateHeader();
  window.addEventListener("scroll", updateHeader, { passive: true });
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateHeader);
});
</script>

<template>
  <header class="site-header" :class="{ 'is-scrolled': isScrolled }">
    <a class="brand" href="#top" aria-label="青炉餐厅首页" @click="closeMenu">
      <span class="brand-mark">Q</span>
      <span>青炉</span>
    </a>

    <button
      class="nav-toggle"
      type="button"
      :aria-label="navToggleLabel"
      :aria-expanded="String(isMenuOpen)"
      @click="toggleMenu"
    >
      <span></span>
      <span></span>
    </button>

    <nav class="main-nav" :class="{ 'is-open': isMenuOpen }">
      <a v-for="item in navItems" :key="item.href" :href="item.href" @click="closeMenu">
        {{ item.label }}
      </a>
    </nav>
  </header>

  <main id="top">
    <section class="hero" aria-labelledby="hero-title">
      <div class="hero-media" role="img" aria-label="餐厅木桌上的精致晚餐"></div>
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <p class="eyebrow">Seasonal Dining · Since 2026</p>
        <h1 id="hero-title">青炉餐厅</h1>
        <p class="hero-copy">把本地时令、炭火香气和一杯好酒，收进一张从容的城市餐桌。</p>
        <div class="hero-actions">
          <a class="button button-primary" href="#reserve">预约今晚</a>
          <a class="button button-secondary" href="#menu">查看菜单</a>
        </div>
      </div>
      <aside class="hero-card" aria-label="今日营业信息">
        <span>今日供应</span>
        <strong>18:00 - 22:30</strong>
        <p>晚市套餐 328 / 位起</p>
      </aside>
    </section>

    <section class="intro">
      <div>
        <p class="section-kicker">Fresh, Warm, Quiet</p>
        <h2>一间为晚餐慢下来而开的餐厅</h2>
      </div>
      <p>
        青炉用开放式炭火厨房处理海鲜、蔬菜与熟成肉类。菜单随季节微调，口味克制、层次清晰，适合约会、朋友小聚，也适合认真吃一顿饭。
      </p>
    </section>

    <section class="menu-section" id="menu" aria-labelledby="menu-title">
      <div class="section-heading">
        <p class="section-kicker">Signature Plates</p>
        <h2 id="menu-title">招牌菜单</h2>
      </div>

      <div class="dish-grid">
        <article v-for="dish in dishes" :key="dish.number" class="dish-card">
          <img :src="dish.image" :alt="dish.alt" />
          <div>
            <span>{{ dish.number }}</span>
            <h3>{{ dish.title }}</h3>
            <p>{{ dish.description }}</p>
          </div>
        </article>
      </div>
    </section>

    <section class="story-section" id="story">
      <div class="story-image">
        <img
          src="https://images.unsplash.com/photo-1577219491135-ce391730fb2c?auto=format&fit=crop&w=1000&q=80"
          alt="主厨在厨房准备菜品"
        />
      </div>
      <div class="story-copy">
        <p class="section-kicker">主厨餐桌</p>
        <h2>像回到一间熟悉的厨房，好好吃顿热饭</h2>
        <p>
          我们每天清晨挑选新鲜食材，慢慢熬好汤底，准备刚出炉的面包和甜点。等你入座时，厨房会把温热的香气、刚好的火候和不被打扰的晚餐时光一起端上桌。
        </p>
        <dl class="stats">
          <div v-for="item in stats" :key="item.label">
            <dt>{{ item.value }}</dt>
            <dd>{{ item.label }}</dd>
          </div>
        </dl>
      </div>
    </section>

    <section class="space-section" id="space" aria-labelledby="space-title">
      <div class="section-heading">
        <p class="section-kicker">The Room</p>
        <h2 id="space-title">适合交谈的光线和距离</h2>
      </div>
      <div class="space-gallery">
        <img v-for="image in spaceImages" :key="image.src" :src="image.src" :alt="image.alt" />
      </div>
    </section>

    <section class="reserve-section" id="reserve" aria-labelledby="reserve-title">
      <div>
        <p class="section-kicker">Reservation</p>
        <h2 id="reserve-title">今晚留一张桌</h2>
        <p>建议提前 1 天预约。生日、纪念日或过敏信息可在到店时告知，我们会尽量为你安排。</p>
      </div>
      <form class="reserve-form" @submit.prevent="submitReserve">
        <label>
          日期
          <input type="date" name="date" />
        </label>
        <label>
          人数
          <select name="party">
            <option v-for="option in partyOptions" :key="option">{{ option }}</option>
          </select>
        </label>
        <label>
          手机
          <input type="tel" name="phone" placeholder="138 0000 0000" />
        </label>
        <button class="button button-primary" type="submit">{{ submitText }}</button>
      </form>
    </section>
  </main>

  <footer class="site-footer">
    <span>青炉餐厅 · 上海市梧桐路 118 号</span>
    <span>hello@qinglu.example · 021-8800-2026</span>
  </footer>
</template>
