<template>
  <div class="presentation-cover">
    <h1 class="presentation-cover__title">{{ title }}</h1>
    <h2 class="presentation-cover__subtitle">{{ subtitle }}</h2>
  </div>
</template>

<script>
export default {
  name: 'PresentationCover',
  props: {
    title: String,
    subtitle: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .presentation-cover {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      width: 100%;
      min-height: 100vh;
      /*background-color: rgb(0, 81, 124);*/
      background-color: #2c3e50;
      user-select: none;
    }

    .presentation-cover__title {
      font-size: 100px;
      margin: 0 0 20px;
      color: rgb(10, 194, 163);
    }

    .presentation-cover__subtitle {
      font-size: 50px;
      margin: 0;
      color: #fff;
    }
</style>
