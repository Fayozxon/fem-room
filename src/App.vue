<script>
import HomeView from './views/HomeView.vue';
import Header from './components/Header.vue';

export default {
  components: {HomeView, Header}
}
</script>

<template>

  <main class="main">

    <Header></Header>

    <HomeView></HomeView>

  </main>
</template>

<style lang="scss" scoped>
.main {
  position: relative;
  max-width: 1440px;
  min-height: 100vh;
  margin: 0 auto;
  overflow-x: hidden;

  @media only screen and (max-width: 1100px) {
    max-width: 765px;
  }
}
</style>
