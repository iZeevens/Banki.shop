<template>
  <div class="preloader" v-if="isLoading">
    <div class="spinner"></div>
  </div>
</template>

<script>
import './spinner.css';
export default {
  name: 'PreloaderComponent',
  props: {
    isLoading: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
