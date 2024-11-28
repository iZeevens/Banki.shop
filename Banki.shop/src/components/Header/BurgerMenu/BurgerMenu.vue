<template>
  <div class="burger">
    <button
      class="burger-menu"
      @click="toggleMenu"
      :class="{ active: menuOpen }"
    >
      <span class="burger__menu-line burger-line-1"></span>
      <span class="burger__menu-line burger-line-2"></span>
    </button>
    <nav v-if="menuOpen" class="burger__nav">
      <li class="burger__nav-item">Каталог</li>
      <li class="burger__nav-item">Доставка</li>
      <li class="burger__nav-item">Оплата</li>
      <li class="burger__nav-item">Контакты</li>
      <li class="burger__nav-item">О компании</li>
    </nav>
  </div>
</template>

<script>
import './burgerMenu.css';
export default {
  name: 'PageBurgerMenu',
  data() {
    return {
      menuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
  },
};
</script>
