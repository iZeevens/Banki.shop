<template>
  <div id="app">
    <PageHeader @search="handleSearch" />
    <PageArtGalleryCards :searchQuery="searchQuery" />
    <PageFooter />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import PageHeader from './components/Header/Header.vue';
import PageArtGalleryCards from './components/ArtGalleryCards/ArtGalleryCards.vue';
import PageFooter from './components/Footer/Footer.vue';
import './app.css';

export default Vue.extend({
  name: 'App',
  components: {
    PageHeader,
    PageArtGalleryCards,
    PageFooter,
  },
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    handleSearch(query) {
      this.searchQuery = query;
    },
  },
});
</script>
