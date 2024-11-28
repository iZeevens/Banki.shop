<template>
  <header class="header">
    <div class="container">
      <nav class="header__nav">
        <li class="header__nav-item">Каталог</li>
        <li class="header__nav-item">Доставка</li>
        <li class="header__nav-item">Оплата</li>
        <li class="header__nav-item">Контакты</li>
        <li class="header__nav-item">О компании</li>
      </nav>
      <BurgerMenu />
      <div class="header__search">
        <input
          class="header__search-input"
          type="text"
          id="search"
          name="query"
          placeholder="Поиск по названию картины"
          v-model="searchQuery"
          @keyup.enter="triggerSearch"
        />
        <button class="header__search-button" @click="triggerSearch">
          Найти
        </button>
      </div>
    </div>
  </header>
</template>

<script>
import './header.css';
import BurgerMenu from './BurgerMenu/BurgerMenu.vue';

export default {
  name: 'PageHeader',
  components: { BurgerMenu },
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    triggerSearch() {
      this.$emit('search', this.searchQuery);
    },
  },
};
</script>
