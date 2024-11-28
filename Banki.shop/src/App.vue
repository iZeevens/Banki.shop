<template>
  <div id="app">
    <PageHeader @search="handleSearch" />
    <PageArtGalleryCards :searchQuery="searchQuery" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import PageHeader from './components/Header/PageHeader.vue';
import PageArtGalleryCards from './components/ArtGalleryCards/PageArtGalleryCards.vue';
import './app.css';

export default Vue.extend({
  name: 'App',
  components: {
    PageHeader,
    PageArtGalleryCards,
  },
  data() {
    return {
      searchQuery: '',
      isLoading: true,
    };
  },
  methods: {
    handleSearch(query) {
      this.searchQuery = query;
    },
  },
});
</script>
