<template>
  <div>
    <div class="modal-overlay" v-if="isVisible" @click="closeModal"></div>
    <div class="modal" v-if="isVisible">
      <span class="modal__name">{{ art.name }}</span>
      <span class="modal__description">{{ art.description }}</span>
      <div class="modal__price">
        <span class="modal__price--old">{{ art.oldPrice }}</span>
        <span class="modal__price--new">{{ art.newPrice }}</span>
      </div>
      <div class="modal__slider">
        <img
          class="modal__slider__img"
          :src="art.images[currentImage]"
          alt="Art Image"
        />
      </div>
      <div class="modal__slider__controls">
        <button
          class="modal__slider__controls--left"
          @click="prevImage"
        ></button>
        <button
          class="modal__slider__controls--right"
          @click="nextImage"
        ></button>
      </div>
    </div>
  </div>
</template>

<script>
import './modalWindow.css';

export default {
  name: 'PageModalWindow',
  props: {
    art: {
      type: Object,
      required: true,
    },
    isVisible: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      currentImage: 0,
    };
  },
  methods: {
    closeModal() {
      this.$emit('update:isVisible', false);
    },
    nextImage() {
      if (this.art.images.length - 1 === this.currentImage) {
        return (this.currentImage = 0);
      }

      this.currentImage += 1;
    },

    prevImage() {
      if (this.currentImage === 0) {
        return (this.currentImage = this.art.images.length - 1);
      }

      this.currentImage -= 1;
    },
  },
};
</script>
