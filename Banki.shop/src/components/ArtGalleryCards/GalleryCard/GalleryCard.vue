<template>
  <div class="art-card">
    <img class="art-card__image" :src="imageSrc" />
    <span class="art-card__name">{{ name }}</span>
    <div class="art-card__details">
      <div class="art-card__price">
        <span>{{ price }}</span>
      </div>
      <div class="art-card__action">
        <button class="art-card__buy-button">Купить</button>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import './galleryCard.css';
export default Vue.extend({
  name: 'GalleryCard',
  props: {
    imageSrc: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    price: {
      type: String,
      required: true,
    },
  },
});
</script>
