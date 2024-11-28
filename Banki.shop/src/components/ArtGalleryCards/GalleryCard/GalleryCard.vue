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
          <button
            class="art-card__buy-button"
            :class="buttonClass"
            @click="handleBuy"
          >
            <img v-if="isPurchased" :src="checkImg" alt="Check" />
            {{ buttonText }}
          </button>
        </div>
      </div>
      <Spinner :isLoading="isLoading" />
    </div>
  </div>
</template>

<script>
import Spinner from '../../ui/Spinner/Spinner.vue';
import checkImg from '../../../public/check_img.png';
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
      isPurchased: false,
      checkImg,
    };
  },
  computed: {
    buttonText() {
      return this.isPurchased ? 'В корзине' : 'Купить';
    },
    buttonClass() {
      return this.isPurchased ? 'purchased' : '';
    },
  },
  created() {
    const purchasedItems =
      JSON.parse(localStorage.getItem('purchasedItems')) || [];
    this.isPurchased = purchasedItems.includes(this.name);
  },
  methods: {
    handleBuy() {
      this.isLoading = true;
      setTimeout(() => {
        this.isLoading = false;
        this.isPurchased = !this.isPurchased;

        let purchasedItems =
          JSON.parse(localStorage.getItem('purchasedItems')) || [];

        if (this.isPurchased) {
          purchasedItems.push(this.name);
        } else {
          purchasedItems = purchasedItems.filter((item) => item !== this.name);
        }

        localStorage.setItem('purchasedItems', JSON.stringify(purchasedItems));
      }, 2000);
    },
  },
};
</script>
