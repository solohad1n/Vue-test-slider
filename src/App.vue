<template>
  <div class="home">
    <div class="sections-menu">
      <span
        class="menu-point"
        v-bind:class="{ active: activeSection == index }"
        v-on:click="scrollToSection(index)"
        v-for="(offset, index) in offsets"
        v-bind:key="index"
      >
      </span>
    </div>
    <section class="fullpage white">
      <div class="fons">
        <header>
          <Header />
        </header>
        <main>
          <div class="container">
            <div class="hero">
              <div class="hero__content">
                <h1 class="hero__title">ОНИ ДОЛЖНЫ ЧТО-ТО ЗНАТЬ</h1>
              </div>
            </div>
            <div class="slider">
              <div class="slider__content">
                <Slider />
              </div>
            </div>
            <div class="search-promo">
              <div class="search-promo__content">
                <SearchPromo />
              </div>
            </div>
          </div>
        </main>
      </div>
    </section>
    <section class="fullpage black">
      <div class="fons">
        <header>
          <Header />
        </header>
        <main>
          <div class="container">
            <div class="hero">
              <div class="hero__content">
                <h1 class="hero__title">ОНИ ДОЛЖНЫ ЧТО-ТО ЗНАТЬ</h1>
              </div>
            </div>
            <div class="slider">
              <div class="slider__content">
                <Slider />
              </div>
            </div>
            <div class="search-promo">
              <div class="search-promo__content">
                <SearchPromo />
              </div>
            </div>
          </div>
        </main>
      </div>
    </section>
    <section class="fullpage red">
      <div class="fons">
        <header>
          <Header />
        </header>
        <main>
          <div class="container">
            <div class="hero">
              <div class="hero__content">
                <h1 class="hero__title">ОНИ ДОЛЖНЫ ЧТО-ТО ЗНАТЬ</h1>
              </div>
            </div>
            <div class="slider">
              <div class="slider__content">
                <Slider />
              </div>
            </div>
            <div class="search-promo">
              <div class="search-promo__content">
                <SearchPromo />
              </div>
            </div>
          </div>
        </main>
      </div>
    </section>
    <section class="fullpage green">
      <div class="fons">
        <header>
          <Header />
        </header>
        <main>
          <div class="container">
            <div class="hero">
              <div class="hero__content">
                <h1 class="hero__title">ОНИ ДОЛЖНЫ ЧТО-ТО ЗНАТЬ</h1>
              </div>
            </div>
            <div class="slider">
              <div class="slider__content">
                <Slider />
              </div>
            </div>
            <div class="search-promo">
              <div class="search-promo__content">
                <SearchPromo />
              </div>
            </div>
          </div>
        </main>
      </div>
    </section>
  </div>
</template>

<script>
import Header from "./components/Header/Header.vue";
import Slider from "./components/Slider/Slider.vue";
import SearchPromo from "./components/Search-promo/Search-promo.vue";

export default {
  name: "HomeView",
  data() {
    return {
      inMove: false,
      activeSection: 0,
      offsets: [],
      touchStartY: 0,
    };
  },
  methods: {
    calculateSectionOffsets() {
      let sections = document.getElementsByTagName("section");
      let length = sections.length;
      for (let i = 0; i < length; i++) {
        let sectionOffset = sections[i].offsetTop;
        this.offsets.push(sectionOffset);
      }
    },
    handleMouseWheel: function (e) {
      if (e.wheelDelta < 30 && !this.inMove) {
        this.moveUp();
      } else if (e.wheelDelta > 30 && !this.inMove) {
        this.moveDown();
      }
      e.preventDefault();
      return false;
    },
    handleMouseWheelDOM: function (e) {
      if (e.detail > 0 && !this.inMove) {
        this.moveUp();
      } else if (e.detail < 0 && !this.inMove) {
        this.moveDown();
      }
      return false;
    },
    moveDown() {
      this.inMove = true;
      this.activeSection--;
      if (this.activeSection < 0) this.activeSection = this.offsets.length - 1;
      this.scrollToSection(this.activeSection, true);
    },
    moveUp() {
      this.inMove = true;
      this.activeSection++;
      if (this.activeSection > this.offsets.length - 1) this.activeSection = 0;
      this.scrollToSection(this.activeSection, true);
    },
    scrollToSection(id, force = false) {
      if (this.inMove && !force) return false;
      this.activeSection = id;
      this.inMove = true;
      document
        .getElementsByTagName("section")
        [id].scrollIntoView({ behavior: "smooth" });
      setTimeout(() => {
        this.inMove = false;
      }, 400);
    },
    touchStart(e) {
      e.preventDefault();
      this.touchStartY = e.touches[0].clientY;
    },
    touchMove(e) {
      if (this.inMove) return false;
      e.preventDefault();
      const currentY = e.touches[0].clientY;
      if (this.touchStartY < currentY) {
        this.moveDown();
      } else {
        this.moveUp();
      }
      this.touchStartY = 0;
      return false;
    },
  },
  mounted() {
    this.calculateSectionOffsets();
    window.addEventListener("DOMMouseScroll", this.handleMouseWheelDOM); // Mozilla Firefox
    window.addEventListener("mousewheel", this.handleMouseWheel, {
      passive: false,
    }); // Other browsers
    window.addEventListener("touchstart", this.touchStart, { passive: false }); // mobile devices
    window.addEventListener("touchmove", this.touchMove, { passive: false }); // mobile devices
  },
  destroyed() {
    window.removeEventListener("mousewheel", this.handleMouseWheel, {
      passive: false,
    }); // Other browsers
    window.removeEventListener("DOMMouseScroll", this.handleMouseWheelDOM); // Mozilla Firefox
    window.removeEventListener("touchstart", this.touchStart); // mobile devices
    window.removeEventListener("touchmove", this.touchMove); // mobile devices
  },
  components: { Header, Slider, SearchPromo },
};
</script>

<style>
@import "../src/assets/CSS/style.css";
.container {
  max-width: 900px;
  margin: 0 auto;
}
.hero__title {
  font-family: "Futura";
  font-style: normal;
  font-weight: 700;
  font-size: 45px;
  letter-spacing: -0.692308px;
  color: #ffcc64;
  margin: 0 0 20px 0;
  text-align: center;
}
body {
  margin: 0;
  overflow: hidden;
}

.fullpage {
  height: 100vh;
  width: 100%;
}

h1 {
  margin: 0;
}

.red {
  background-color: #ab4545;
}

section.black {
  background-color: #000;
}

.white {
  background: url("../src/assets/Sky.png") no-repeat center;
  background-size: cover;
  min-height: 100vh;
  background-color: white;
}
.fons {
  background: url("../src/assets/Group 4.png") no-repeat center;
  background-size: cover;
  min-height: 100vh;
}

.green {
  background-color: #68c368;
}

.sections-menu {
  position: fixed;
  left: 1rem;
  top: 50%;
  transform: translateY(-50%);
}

.sections-menu .menu-point {
  width: 8px;
  height: 2.03px;
  background-color: #333333;
  display: block;
  margin: 3.5rem 0;
  transition: 0.4s ease all;
  cursor: pointer;
}

.sections-menu .menu-point.active {
  width: 116px;
  height: 2px;
}
</style>
