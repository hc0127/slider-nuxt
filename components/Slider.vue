<template>
  <div class="slider-content">
    <swiper ref="refSwiper" :loop="true" :slidesPerView="4" :spaceBetween="30" :watchSlidesProgress="true"
      :navigation="true" :modules="modules" @autoplayTimeLeft="onAutoplayTimeLeft" @slideChange="handleSlideChange"
      :autoplay="{
        delay: 3000,
        disableOnInteraction: false,
      }" class="mySlider">
      <div class="slider-description-content">
        <h1>Benefits</h1>
        <h2 class="slider_description_title">{{ datas[activeIndex].title }}</h2>
        <p class="slider_description">{{ datas[activeIndex].description }}</p>
      </div>
      <swiper-slide v-for="(data, index) in datas" :key=index><img :src=data.img :alt=data.img /></swiper-slide>
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
  props: {
    datas: []
  },
  data() {
    return {
      activeIndex: 0,
      modules: [Autoplay, Navigation],
    }
  },
  methods: {
    handleSlideChange(swiper) {
      const activeIndex = swiper.activeIndex && (swiper.previousRealIndex + 1) % this.datas.length;
      this.activeIndex = activeIndex;
    },
  },
  setup(props) {
    const progressCircle = ref(null);
    const onAutoplayTimeLeft = (s, time, progress) => {
      progressCircle.value.style.setProperty('--progress', 1 - progress);
    };

    return {
      onAutoplayTimeLeft,
      progressCircle,
    };
  },

};
</script>
