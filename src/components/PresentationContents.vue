<template>
  <div class="presentation-contents">
    <h2 class="presentation-contents__title">{{ title }}:</h2>
    <ul class="presentation-contents__menu">
      <li
        v-for="item, index in contents"
        class="presentation-contents__menu-item"
        :key="`menu-item_${index}`"
      >
        <button
          class="presentation-contents__menu-button"
          @click.stop.prevent="setCurrentSlide(item.id)"
        >
          {{ item.title }}
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'PresentationContents',
  props: {
    title: String,
    contents: Array
  },
  methods: {
    setCurrentSlide(slideId) {
      this.$emit('setSlide', slideId);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .presentation-contents {
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
      flex-direction: column;
      width: 100%;
      height: 100%;
      background-color: rgb(0, 81, 124);
      user-select: none;
      padding: 50px 100px;
      box-sizing: border-box;
    }

    .presentation-contents__title {
      font-size: 60px;
      margin: 0;
      color: #fff;
      line-height: 120px;
      position: relative;
    }

    .presentation-contents__title::before {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 70px;
      border-bottom: 5px solid #038dd1;
    }

    .presentation-contents__content {
      font-size: 40px;
      margin: 0;
      /* color: rgb(10, 194, 163); */
      color: #fff;
      text-align: left;
    }

    .presentation-contents__menu {
      list-style-type: square;
      margin: 40px 0;
    }

    .presentation-contents__menu-item {
      font-size: 40px;
      margin: 0;
      color: rgb(10, 194, 163);
      text-align: left;
      margin-bottom: 10px;
    }

    .presentation-contents__menu-button {
      background: transparent;
      border: none;
      border-spacing: 0;
      margin: 0;
      padding: 0;
      text-decoration: none;
      text-indent: 0;
      color: inherit;
      outline: none;
      font-size: 40px;
      text-align: left;
      cursor: pointer;
      border-bottom: 5px solid transparent;
    }

    .presentation-contents__menu-button:hover {
      border-bottom-color: rgb(10, 194, 163);
    }
</style>
