<template>
  <div class="art-card" :class="{ sold: isSold }">
    <img
      class="art-card__image"
      :src="imageSrc"
      alt="Art Image"
      @click="handleClick"
    />
    <div class="art-card__container">
      <span class="art-card__name" @click="handleClick">{{ name }}</span>
      <div class="art-card__details">
        <span v-if="isSold" class="art-card__sold"> Продана на аукционе</span>
        <template v-else>
          <div class="art-card__price">
            <span class="art-card__price--old">{{ oldPrice }}</span>
            <span class="art-card__price--new">{{ newPrice }}</span>
          </div>
          <div class="art-card__action">
            <button
              class="art-card__buy-button"
              :class="buttonClass"
              @click="handleBuy"
            >
              <img
                v-if="isPurchased"
                :src="require('../../../public/check_img.png')"
                alt="Check"
              />
              {{ buttonText }}
            </button>
          </div>
        </template>
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
    isSold: {
      type: Boolean,
      required: false,
    },
  },
  components: { Spinner },
  data() {
    return {
      isLoading: false,
      isPurchased: false,
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
    handleClick() {
      this.$emit('click', this);
    },
  },
};
</script>
