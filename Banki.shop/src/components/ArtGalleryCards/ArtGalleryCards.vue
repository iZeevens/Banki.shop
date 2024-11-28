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
          imageSrc:
            'https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg/800px-Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg',
          images: [
            'https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg/800px-Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg',
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTmZxUmMcJqs26sq93NqnGlAWI37PTRuJWKHQ&s',
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTBPTfmtPp6llRRntIY_CMjlNYigqB-HYc0sg&s',
          ],
          name: '«Рождение Венеры» Сандро Боттичелли',
          description:
            'Картина итальянского художника флорентийской школы Сандро Боттичелли. Представляет собой живопись темперой на холсте размером 172,5 x 278,5 см. В настоящее время хранится в галерее Уффици, Флоренция',
          newPrice: '1 000 000$',
          oldPrice: '2 000 000$',
        },
        {
          imageSrc:
            'https://avatars.dzeninfra.ru/get-zen_doc/3642096/pub_603bd2a482fc21754d231dd5_603bd2b882fc21754d235789/scale_1200',
          images: [
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://avatars.dzeninfra.ru/get-zen_doc/3642096/pub_603bd2a482fc21754d231dd5_603bd2b882fc21754d235789/scale_1200',
            'https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg/800px-Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg',
          ],
          name: '«Тайная вечеря»  Леонардо да Винчи',
          description:
            'Монументальная роспись работы Леонардо да Винчи, изображающая сцену последней трапезы Христа со своими учениками. Создана в 1495—1498 годы в доминиканском монастыре Санта-Мария-делле-Грацие в Милане',
          newPrice: '3 000 000$',
        },
        {
          imageSrc:
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTdPtYHfVR-nHm9bA2HBpeTMCVWmb_BN8xcQ&s',
          images: [
            'https://avatars.dzeninfra.ru/get-zen_doc/3642096/pub_603bd2a482fc21754d231dd5_603bd2b882fc21754d235789/scale_1200',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTdPtYHfVR-nHm9bA2HBpeTMCVWmb_BN8xcQ&s',
          ],
          name: '«Сотворение Адама» Микеланджело',
          description:
            'фреска Микеланджело Буонарроти на потолке Сикстинской капеллы (Ватикан), созданная им около 1511-1512 лет. Это - одна из центральных композиций, иллюстрирующую создании человека Богом. Эта работа является одним из самых известных произведений искусства, ее сюжет часто ссылаются и пародируют',
          newPrice: '6 000 000$',
          oldPrice: '5 000 000$',
        },
        {
          imageSrc:
            'https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Rembrandt_-_The_Anatomy_Lesson_of_Dr_Nicolaes_Tulp.jpg/1200px-Rembrandt_-_The_Anatomy_Lesson_of_Dr_Nicolaes_Tulp.jpg',
          images: [
            'https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Rembrandt_-_The_Anatomy_Lesson_of_Dr_Nicolaes_Tulp.jpg/1200px-Rembrandt_-_The_Anatomy_Lesson_of_Dr_Nicolaes_Tulp.jpg',
            'https://cdn.nur.kz/images/1120x630/f5f1fbe856ddf827.jpeg',
            'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTdPtYHfVR-nHm9bA2HBpeTMCVWmb_BN8xcQ&s',
          ],
          name: '«Урок анатомии»  Рембрандт',
          description:
            'Картина выдающегося голландского живописца Рембрандта ван Рейна, написанная в 1632 году',
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
