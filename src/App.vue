<template>
  <!--<img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <div
    class="presentation-wrapper"
    ref="wrapper"
    tabindex="0"
    @keydown.left="goToPrevSlide"
    @keydown.right="goToNextSlide"
    @keydown.up="goToPrevSlide"
    @keydown.down="goToNextSlide"
  >
    <PresentationCover
      v-if='currentSlideNumber === 0'
      :title="title"
      :subtitle="subtitle"
      @click="goToNextSlide"
    />

    <PresentationContents
      v-if='currentSlideNumber === 1'
      :title="contentsTitle"
      :contents="contents"
      @setSlide="setCurrentSlide"
      @click="goToNextSlide"
    />

    <PresentationSlide
      v-if='currentSlideNumber > 1'
      :slide="currentSlide"
      @click="goToNextSlide"
    />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import PresentationCover from './components/PresentationCover.vue';
import PresentationContents from './components/PresentationContents.vue';
import PresentationSlide from './components/PresentationSlide.vue';

export default {
  name: 'App',
  components: {
    // HelloWorld,
    PresentationCover,
    PresentationContents,
    PresentationSlide
  },
  data: () => {
    return {
      currentSlideNumber: 0,
      title: 'Vue.js',
      subtitle: 'Основы',
      contentsTitle: 'Содержание',
      slides: [
        {
          id: 2,
          title: 'Преимущества Vue',
          content: '<ul><li>Быстрота</li><li>Vue.js - это фреймворк</li><li>Двухстороннее связывание</li><li>Реактивность</li><li>Поддержка JS и Typescript</li></ul>'
        },
        {
          id: 3,
          title: 'Установка, быстрый старт',
          content: '<ul><li>Подключение напрямую через CDN</li><li>Установка через NPM</li><li>Установка через Vue CLI</li></ul>'
        },
        {
          id: 4,
          title: 'Базовая архитектура приложения',
          content: '<ul><li>Структура папок</li><li>Основные файлы</li></ul>'
        },
        {
          id: 5,
          title: 'Компоненты, их свойства и методы',
          content: ''
        },
        {
          id: 6,
          title: 'Vuex',
          content: ''
        },
        {
          id: 7,
          title: 'Vue router',
          content: ''
        },
        {
          id: 8,
          title: 'Vue devtools',
          content: ''
        },
      ]
    };
  },
  computed: {
    currentSlide() {
      return this.slides.find(slide => slide.id === this.currentSlideNumber);
    },

    contents() {
      return this.slides.map((slide) => {
        const { id, title } = slide;

        return {
          id,
          title
        }
      });
    }
  },
  methods: {
    goToPrevSlide() {
      if (this.currentSlideNumber !== 0) {
        this.currentSlideNumber--;
      }
    },

    goToNextSlide() {
      if (this.currentSlideNumber < this.slides.length + 1) {
        this.currentSlideNumber++;
      }
    },

    setCurrentSlide(slideId) {
      this.currentSlideNumber = slideId;
    }
  },
  mounted() {
    this.$refs['wrapper'].focus();
  }
}
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
