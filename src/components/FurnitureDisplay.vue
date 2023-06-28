<script>
export default {
  data() {
    return {
      activeImgNum: 1,
      infoTexts: [
        {
          title: 'Discover innovative ways to decorate',
          text: 'We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.'
        },
        {
          title: 'We are available all across the globe',
          text: 'With stores all over the world, it\'s easy for you to find furniture for your home or place of business. Locally, we’re store locator. Any questions? Don\'t hesitate to contact us today.'
        },
        {
          title: 'Manufactured with the best materials',
          text: 'Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.'
        }
      ]
    }
  },
  methods: {
    nextImg() {
      if (this.activeImgNum == 3) {
        this.activeImgNum = 1;
      } else {
        this.activeImgNum++;
      }
    },
    prevImg() {
      if (this.activeImgNum == 1) {
        this.activeImgNum = 3;
      } else {
        this.activeImgNum--;
      }
    }
  }
}
</script>

<template>

  <section class="furniture-section">
    <!-- preloading -->
    <img
        v-for="n in 3"
        :src="`/desktop-image-hero-${n}.jpg`"
        :alt="`Furniture Image ${n}`"
        style="display: none;"
        preloading>
    <!-- image -->
    <transition mode="out-in" name="fade" class="furniture-section__img">
      <img
        :src="`/desktop-image-hero-${activeImgNum}.jpg`"
        :alt="`Furniture Image ${activeImgNum}`"
        :key="activeImgNum">
    </transition>
    <!-- info -->
    <div class="furniture-section__info">
      <transition mode="out-in" name="fade">
        <div :key="activeImgNum-1">
          <h1 class="title">{{ infoTexts[activeImgNum-1].title }}</h1>
          <p class="text">
            {{ infoTexts[activeImgNum-1].text }}
          </p>
        </div>
      </transition>
      <a href="#!" class="btn">
        Shop now
        <svg width="40" height="12" xmlns="http://www.w3.org/2000/svg"><path d="M34.05 0l5.481 5.527h.008v.008L40 6l-.461.465v.063l-.062-.001L34.049 12l-.662-.668 4.765-4.805H0v-1h38.206l-4.82-4.86L34.05 0z" fill="#000" fill-rule="nonzero"/></svg>
      </a>
      <div class="buttons">
        <button @click="prevImg"><img src="../assets/images/icon-angle-left.svg"></button>
        <button @click="nextImg"><img src="../assets/images/icon-angle-right.svg"></button>
      </div>
    </div>
  </section>


</template>

<style lang="scss" scoped>
@import '../main.scss';

.furniture-section {
  display: flex;
  background: $white;

  @media only screen and (max-width: 1100px) {
    flex-direction: column;
  }

  &__img {
    position: relative;
    width: 60%;
    height: 60vh;
    max-height: 530px;
    object-fit: cover;

    @media only screen and (max-width: 1100px) {
      width: 100%;
      max-height: 360px;
    }

    img {
      position: absolute;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  &__info {
    position: relative;
    width: 40%;
    display: flex;
    flex-direction: column;
    gap: 30px;
    justify-content: center;
    align-items: center;
    padding-bottom: 50px;

    @media only screen and (max-width: 1100px) {
      width: 100%;
      padding: 56px 16px;
      min-height: 400px;
    }

    .title {
      font-size: $fs-xl;
      font-weight: 700;
      letter-spacing: -2px;
      max-width: 400px;
      padding-bottom: 20px;
    }

    .text {
      color: $dark-gray;
      font-weight: 500;
      line-height: 1.5;
      letter-spacing: -0.5px;
      font-size: $fs-md;
      max-width: 400px;
    }

    .btn {
      text-transform: uppercase;
      text-decoration: none;
      color: $black;
      letter-spacing: 6px;
      font-weight: 700;
      width: 400px;
      transition: $ts-200;

      &:hover {
        color: $dark-gray;

        path {
          fill: $dark-gray;
        }
      }

      svg {
        margin-left: 10px;
        
        path {
          transition: $ts-200;
        }
      }
    }
    
    .buttons {
      position: absolute;
      bottom: 0;
      left: 0;

      @media only screen and (max-width: 1100px) {
        right: 0;
        left: unset;
        bottom: 100%;
      }

      button {
        width: 80px;
        height: 80px;
        border: none;
        background: $black;
        cursor: pointer;
        transition: $ts-200;

        &:hover {
          background: $very-dark-gray;
        }
      }
    }
  }
}

// transitions
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active{
  transition: $ts-200;
}
</style>
