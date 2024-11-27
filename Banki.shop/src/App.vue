<template>
  <div id="app">
    <PageHeader />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import PageHeader from './components/Header/PageHeader.vue';
import './app.css';

export default Vue.extend({
  name: 'App',
  components: {
    PageHeader,
  },
});
</script>
