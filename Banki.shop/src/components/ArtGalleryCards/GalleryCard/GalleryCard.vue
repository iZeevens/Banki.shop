<template>
  <div class="art-card">
    <img class="art-card__image" :src="imageSrc" />
    <div class="art-card__container">
      <span class="art-card__name">{{ name }}</span>
      <div class="art-card__details">
        <div class="art-card__price">
          <span class="art-card__price__old">{{ oldPrice }}</span>
          <span class="art-card__price__new">{{ newPrice }}</span>
        </div>
        <div class="art-card__action">
          <button class="art-card__buy-button" @click="handleBuy">
            Купить
          </button>
        </div>
      </div>
      <Spinner :isLoading="isLoading" />
    </div>
  </div>
</template>

<script>
import Spinner from '../../ui/Spinner/Spinner.vue';
import './galleryCard.css';

export default {
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
  components: { Spinner },
  data() {
    return {
      isLoading: false,
    };
  },
  methods: {
    handleBuy() {
      this.isLoading = true;
      setTimeout(() => {
        this.isLoading = false;
      }, 2000);
    },
  },
};
</script>
