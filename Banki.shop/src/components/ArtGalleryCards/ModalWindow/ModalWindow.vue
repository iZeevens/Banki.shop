<template>
  <div class="modal">
    <button class="modal__close"></button>
    <h2 class="modal__title"></h2>
    <h2 class="modal__description"></h2>
    <div class="modal__price">
      <span class="modal__price__old"></span>
      <span class="modal__price__new"></span>
    </div>
    <div class="modal__slider">
      <img class="modal__slider__img" src="" alt="Art Image" />
      <div class="modal__slider__controls">
        <button class="modal__slider__controls--left"></button>
        <button class="modal__slider__controls--right"></button>
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
};
</script>
