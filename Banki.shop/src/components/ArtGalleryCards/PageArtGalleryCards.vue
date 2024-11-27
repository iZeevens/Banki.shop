<template>
  <main>
    <h2>Картины эпохи Возрождения</h2>
    <div class="cards">
      <GalleryCard :imageSrc="'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg'" :name="'«Рождение Венеры» Сандро Боттичелли'" :newPrice="'1 000 000$'" />
      <GalleryCard :imageSrc="'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg'" :name="'«Рождение Венеры» Сандро Боттичелли'" :newPrice="'1 000 000$'" />
    </div>
  </main>
</template>

<script>
import './pageArtGalleryCards.css';
import GalleryCard from './GalleryCard/GalleryCard.vue';

export default {
  name: 'PageArtGalleryCards',
  components: { GalleryCard },
};
</script>
