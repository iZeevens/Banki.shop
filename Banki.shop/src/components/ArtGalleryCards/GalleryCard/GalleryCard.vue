<!-- Change contain -->
<template>
  <div class="art-card">
    <img class="art-card__image" :src="imageSrc" />
    <div class="art-card__contain">
      <span class="art-card__name">{{ name }}</span>
      <div class="art-card__details">
        <div class="art-card__price">
          <span class="art-card__price__old">{{ oldPrice }}</span>
          <span class="art-card__price__new">{{ newPrice }}</span>
        </div>
        <div class="art-card__action">
          <button class="art-card__buy-button">Купить</button>
        </div>
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
    newPrice: {
      type: String,
      required: true,
    },
    oldPrice: {
      type: String,
      required: false,
    },
  },
});
</script>
