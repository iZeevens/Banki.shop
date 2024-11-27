<template>
  <div class="art-card">
    <img class="art-card__image" src="" alt="" />
    <span class="art-card__name">«Рождение Венеры» Сандро Боттичелли</span>
    <div class="art-card__details">
      <div class="art-card__price">
        <span>1 000 000$</span>
      </div>
      <div class="art-card__action">
        <button class="art-card__buy-button">Купить</button>
      </div>
    </div>
  </div>
</template>

<script>
import './galleryCard.css';
export default {
  name: 'GalleryCard',
};
</script>
