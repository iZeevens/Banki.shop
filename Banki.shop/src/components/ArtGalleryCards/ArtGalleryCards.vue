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
          :isSold="card.isSold"
          @click="openModal(card)"
        />
      </div>
    </div>
    <ModalWindow
      :isVisible="isModalVisible"
      :art="selectedCard"
      @update:isVisible="isModalVisible = $event"
    />
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
      isModalVisible: false,
      selectedCard: null,
      cards: [
        {
          imageSrc: 'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          images: [
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTmZxUmMcJqs26sq93NqnGlAWI37PTRuJWKHQ&s',
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTBPTfmtPp6llRRntIY_CMjlNYigqB-HYc0sg&s',
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
          name: '«Тайная вечеря»  Леонардо да Винчи',
          description: 'bla bla bla',
          newPrice: '3 000 000$',
        },
        {
          imageSrc: 'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          images: [
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          ],
          name: '«Сотворение Адама» Микеланджело',
          description: 'bla bla bla',
          newPrice: '6 000 000$',
          oldPrice: '5 000 000$',
        },
        {
          imageSrc: 'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          images: [
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
          ],
          name: '«Сотворение Адама» Микеланджело',
          description: 'bla bla bla',
          newPrice: '5 000 000$',
          oldPrice: '6 000 000$',
          isSold: true,
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
  methods: {
    openModal(card) {
      this.isModalVisible = true;
      this.selectedCard = card;
    },
  },
};
</script>
