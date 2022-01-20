<template lang="html">
  <section class="portfolio">

    <h3 class="portfolio__title title">Our Awesome Portofolio</h3>

    <div class="portfolio__slider" ref="portfolioWrapper">
      <sliderComponent
        :listLength="5"
        :sliderWrapperSize="portfolioWrapperSize"
        :slideSize="portfolioItemSize"
      >

        <li
          class="portfolio__item"
          v-for="index in 5"
          :key="index"
          :ref="el => { if (el) portfolioItem[index] = el }"
        >
          <span class="portfolio-image-wrapper">
            <img class="portfolio__image" src="../../assets/images/portfolio-image1.png" alt="portfolio-example">
          </span>
          <span class="portfolio-image-wrapper portfolio-image-wrapper1">
            <img class="portfolio__image" src="../../assets/images/portfolio-image2.png" alt="portfolio-example">
          </span>
          <span class="portfolio-image-wrapper portfolio-image-wrapper2">
            <img class="portfolio__image" src="../../assets/images/portfolio-image3.png" alt="portfolio-example">
          </span>
        </li>

      </sliderComponent>
    </div>

    <circleIcon class="portfolio__circle icon-circle" />
    <zigzagIcon class="portfolio__zigzag icon-zigzag" />

  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import circleIcon from '../icons/circle-icon'
import zigzagIcon from '../icons/zigzag-icon'
import sliderComponent from '../technical/slider-component'

const portfolioWrapper = ref(null)
const portfolioWrapperSize = ref(0)

const portfolioItem = ref([])
const portfolioItemSize = ref(0)

onMounted(() => {
  portfolioWrapperSize.value = portfolioWrapper.value.clientWidth
  portfolioItemSize.value = portfolioItem.value[1].clientWidth
})

</script>
