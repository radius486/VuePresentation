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
          content: '<ul><li><span>Подключение напрямую через CDN</span><img style="margin-top: 10px;" height=30 src="images/script1.png"></li><li><span>Установка через NPM</span></br><code>npm install vue</code></li><li><span>Установка через Vue CLI</span></br><code>npm install -g @vue/cli</code></li></ul>'
        },
        {
          id: 4,
          title: 'Базовая архитектура приложения',
          content: '<ul><li>Структура папок</li><li>Основные файлы</li></ul>'
        },
        {
          id: 5,
          title: 'Компоненты',
          content: '<ul><li>Структура компонента</li><li>Данные</li><li>Вычисляемые свойства</li><li>Методы</li><li>Наблюдатели</li><li>Директивы</li><li>Свойства</li></ul>'
        },
        {
          id: 6,
          title: 'Хуки Жизненного цикла компонента',
          content: `<div class="flex-row"><ul><li>beforeCreate</li><li>created</li><li>beforeMount</li><li>mounted</li><li>beforeUpdate</li><li>updated</li><li>beforeUnmount</li><li>unmounted</li></ul><img height=500 style="background: #fff;" src="images/livecycle.png"></div>`
        },
        {
          id: 7,
          title: 'Vuex',
          content: ''
        },
        {
          id: 8,
          title: 'Vue router',
          content: ''
        },
        {
          id: 9,
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
    },

    setFocus() {
      this.$refs['wrapper'].focus();
    }
  },
  mounted() {
    this.setFocus();
  },
  updated() {
    this.setFocus();
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
