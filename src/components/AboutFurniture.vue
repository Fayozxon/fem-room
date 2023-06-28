<script>
</script>

<template>

  <section class="about-section">
    <!-- img -->
    <img src="../assets/images/image-about-dark.jpg" class="about-section__img" alt="Dark image">
    <!-- info -->
    <div class="about-section__info">
      <h2 class="title">About our furniture</h2>
      <p class="text">
        Our multifunctional collection blends design and function to suit your individual taste. Make each room unique, or pick a cohesive theme that best express your interests and what inspires you. Find the furniture pieces you need, from traditional to contemporary styles or anything in between. Product specialists are available to help you create your dream space.
      </p>
    </div>
    <!-- img -->
    <img src="../assets/images/image-about-light.jpg" class="about-section__img" alt="Light image">
  </section>

</template>

<style lang="scss" scoped>
@import '../main.scss';

.about-section {
  display: flex;
  background: $white;

  @media only screen and (max-width: 1100px) {
    flex-direction: column;

    & > img {
      width: 100%;
    }
  }

  &__img {
    width: 29%;
  }

  &__info {
    width: 42%;
    padding: 60px 50px;

    @media only screen and (max-width: 1100px) {
      width: 100%;
    }

    .title {
      padding-bottom: 15px;
      text-transform: uppercase;
      font-weight: 700;
      letter-spacing: 6px;
    }

    .text {
      color: $dark-gray;
      font-weight: 500;
      line-height: 1.5;
      letter-spacing: -0.5px;
      font-size: $fs-md;
    }
  }
}
</style>
