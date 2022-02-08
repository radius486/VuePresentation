<template>
  <div class="presentation-cover">
    <div class="presentation-cover__content">
      <h1 class="presentation-cover__title">{{ title }}</h1>
      <h2 class="presentation-cover__subtitle">{{ subtitle }}</h2>
    </div>
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
  position: relative;
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

.presentation-cover__content {
  padding: 100px 200px;
  position: relative;
  background-color: #2c3e50;
}

.presentation-cover__content::before,
.presentation-cover__content::after {
  content: '';
  display: block;
  position: absolute;
  width: 100px;
  height: 100px;
}

.presentation-cover__content::before {
  left: -5px;
  top: -5px;
  border-left: 5px solid #038dd1;
  border-top: 5px solid #038dd1;
}

.presentation-cover__content::after {
  right: -5px;
  bottom: -5px;
  border-right: 5px solid #038dd1;
  border-bottom: 5px solid #038dd1;
}

</style>
