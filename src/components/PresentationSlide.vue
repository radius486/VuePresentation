<template>
  <div class="presentation-slide">
    <h2 class="presentation-slide__title">{{ slide.title }}</h2>
    <div class="presentation-slide__content" v-html="slide.content"></div>
  </div>
</template>

<script>
export default {
  name: 'PresentationSlide',
  props: {
    slide: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .presentation-slide {
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
      flex-direction: column;
      width: 100%;
      min-height: 100vh;
      background-color: rgb(0, 81, 124);
      user-select: none;
      padding: 50px 100px;
      box-sizing: border-box;
    }

    .presentation-slide__title {
      font-size: 60px;
      margin: 0;
      color: #fff;
      line-height: 120px;
      position: relative;
    }

    .presentation-slide__title::before {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 70px;
      border-bottom: 5px solid rgb(10, 194, 163);
    }

    .presentation-slide__content {
      font-size: 40px;
      margin: 0;
      /* color: rgb(10, 194, 163); */
      color: #fff;
      text-align: left;
    }

    ::v-deep ul {
        margin-right: 100px;
    }

    ::v-deep li {
        margin-bottom: 10px;
        list-style-type: square;
    }

    ::v-deep code {
      color: rgb(18, 236, 84);
    }

    ::v-deep img {
      /* max-height: 70vh; */
    }

    ::v-deep .flex-row {
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
    }

    ::v-deep .flex-column {
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
      flex-direction: column;
    }

</style>
