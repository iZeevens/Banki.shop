<template>
  <main>
    <h2>Картины эпохи Возрождения</h2>
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
  </main>
</template>

<script>
import './pageArtGalleryCards.css';
import GalleryCard from './GalleryCard/GalleryCard.vue';

export default {
  name: 'PageArtGalleryCards',
  components: { GalleryCard },
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
          name: '«Рождение Венеры» Сандро Боттичелли',
          newPrice: '1 000 000$',
        },
        {
          imageSrc: 'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          name: '«Мона Лиза» Леонардо да Винчи',
          newPrice: '2 000 000$',
          oldPrice: '2 500 000$',
        },
      ],
    };
  },
  computed: {
    filteredCards() {
      const query = this.searchQuery.toLowerCase();
      console.log(this.cards);
      return this.cards.filter((card) =>
        card.name.toLowerCase().includes(query),
      );
    },
  },
};
</script>
