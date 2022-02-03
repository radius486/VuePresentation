<template>
  <!--<img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>-->

  <PresentationCover
    v-if='currentSlideNumber === 0'
    :title="title"
    :subtitle="subtitle"
    @click="setCurrentSlide"
  />

  <PresentationSlide
    v-if='currentSlideNumber > 0'
    :slide="currentSlide"
    @click="setCurrentSlide"
  />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import PresentationCover from './components/PresentationCover.vue';
import PresentationSlide from './components/PresentationSlide.vue';
// import PresentationSlide from './components/PresentationSlide.vue';

export default {
  name: 'App',
  components: {
    // HelloWorld,
    PresentationCover,
    PresentationSlide,
    // PresentationSlide
  },
  data: () => {
    return {
      currentSlideNumber: 0,
      title: 'Vue.js',
      subtitle: 'Основы',
      contentsTitle: 'Содержание',
      slides: [
        {
          id: 1,
          title: 'Преимущества Vue',
          content: '<ul><li>Быстрота</li><li>Vue.js - это фреймворк</li><li>Двухстороннее связывание</li><li>Реактивность</li><li>Поддержка JS и Typescript</li></ul>'
        },
        {
          id: 2,
          title: 'Установка, быстрый старт',
          content: '<ul><li>Подключение напрямую через CDN</li><li>Установка через NPM</li><li>Установка через Vue CLI</li></ul>'
        },
        {
          id: 3,
          title: 'Базовая архитектура приложения',
          content: '<ul><li>Структура папок</li><li>Основные файлы</li></ul>'
        },
        {
          id: 4,
          title: 'Компоненты, их свойства и методы',
          content: ''
        },
        {
          id: 5,
          title: 'Vuex',
          content: ''
        },
        {
          id: 6,
          title: 'Vue router',
          content: ''
        },
        {
          id: 7,
          title: 'Vue devtools',
          content: ''
        },
      ]
    };
  },
  computed: {
    currentSlide() {
      return this.slides.find(slide => slide.id === this.currentSlideNumber);
    }
  },
  methods: {
    setCurrentSlide() {
      if (this.currentSlideNumber < this.slides.length) {
          this.currentSlideNumber++;
      } else {
          this.currentSlideNumber = 0;
      }

    }
  }
}
</script>

<style>
html, body {
    margin: 0;
    padding: 0;
    height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>
