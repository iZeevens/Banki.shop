<template>
  <main class="main">
    <div class="container">
      <h2 class="main__name">Картины эпохи Возрождения</h2>
      <div class="cards">
        <GalleryCard
          v-for="card in filteredCards"
          :key="card.name"
          :imageSrc="card.imageSrc"
          :name="card.name"
          :newPrice="card.newPrice"
          :oldPrice="card.oldPrice"
        />
      </div>
    </div>
    <ModalWindow :isVisible="true" :art="cards[0]" />
  </main>
</template>

<script>
import './artGalleryCards.css';
import GalleryCard from './GalleryCard/GalleryCard.vue';
import ModalWindow from './ModalWindow/ModalWindow.vue';

export default {
  name: 'PageArtGalleryCards',
  components: { GalleryCard, ModalWindow },
  props: {
    searchQuery: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      cards: [
        {
          imageSrc: 'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          images: [
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          ],
          name: '«Рождение Венеры» Сандро Боттичелли',
          description: 'bla bla bla',
          newPrice: '1 000 000$',
          oldPrice: '2 000 000$',
        },
        {
          imageSrc: 'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          images: [
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          ],
          name: '«Мона Лиза» Леонардо да Винчи',
          description: 'bla bla bla',
          newPrice: '2 000 000$',
          oldPrice: '2 500 000$',
        },
      ],
    };
  },
  computed: {
    filteredCards() {
      const query = this.searchQuery.toLowerCase();
      return this.cards.filter((card) =>
        card.name.toLowerCase().includes(query),
      );
    },
  },
};
</script>
