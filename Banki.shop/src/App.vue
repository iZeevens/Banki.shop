<template>
  <div id="app">
    <PageHeader />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

import PageHeader from './components/Header/PageHeader.vue';

export default Vue.extend({
  name: 'App',
  components: {
    PageHeader,
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
