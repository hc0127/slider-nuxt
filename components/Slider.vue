<template>
  <div class="slider-content">
    <swiper :loop="true" :slidesPerView="4" :spaceBetween="30" :watchSlidesProgress="true" :autoplay="{
      delay: 5000,
      disableOnInteraction: false,
    }" :navigation="true" :modules="modules" @autoplayTimeLeft="onAutoplayTimeLeft" class="mySlider">
      <div class="slider-description-content"></div>
      <swiper-slide>Slide 1</swiper-slide>
      <swiper-slide>Slide 2</swiper-slide>
      <swiper-slide>Slide 3</swiper-slide>
      <swiper-slide>Slide 4</swiper-slide>
      <swiper-slide>Slide 5</swiper-slide>
      <swiper-slide>Slide 6</swiper-slide>
      <template #container-end>
        <div class="autoplay-progress">
          <svg viewBox="0 0 64 64" ref="progressCircle">
            <circle cx="32" cy="32" r="30"></circle>
          </svg>
          <span ref="progressContent"></span>
        </div>
      </template>
    </swiper>
    <p class="append-buttons"></p>
  </div>
</template>
<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';

import 'swiper/css/navigation';

import './style.css';

// import required modules
import { Autoplay, Navigation } from 'swiper/modules';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    const progressCircle = ref(null);
    const onAutoplayTimeLeft = (s, time, progress) => {
      progressCircle.value.style.setProperty('--progress', 1 - progress);
    };

    return {
      onAutoplayTimeLeft,
      progressCircle,
      modules: [Autoplay, Navigation],
    };
  },
};
</script>
