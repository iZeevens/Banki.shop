<template>
  <main>
    <h2>Картины эпохи Возрождения</h2>
    <div class="cards">
      <GalleryCard />
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
