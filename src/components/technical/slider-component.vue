<template lang="html">

  <ul
    class="portfolio__list"
    :style="sliderStyleMove"
  >

    <slot></slot>

  </ul>

  <div class="portfolio__toggler-wrapper">
    <button class="portfolio__toggler portfolio__toggler_left" type="button" name="button" @click="sliderToggle(1)">
      <togglerIcon />
    </button>
    <button class="portfolio__toggler portfolio__toggler_right" type="button" name="button" @click="sliderToggle(-1)">
      <togglerIcon />
    </button>
  </div>

</template>

<script setup>
import { defineProps, ref, computed } from 'vue'
import togglerIcon from '../icons/toggler-icon'

const props = defineProps({
  listLength: Number,                       //Количество элементов
  slideSize: Number,                        //Размер одного элемента
  sliderWrapperSize: Number                //Размер обертки
})

const currentSlide = ref(0)                //Текущий слайд
const MARGIN = 30                           //Отступы между слайдами

const currentSide = ref(0)                   //Сторона в которую листается слайд

function sliderToggle(side) {                 //Функция для переключения слайда

  currentSide.value = side

  if(sliderLimit.value == 'noLimit') {          //Если нету лимитов -> вращаем слайдер
    currentSlide.value += side;
  } else if(sliderLimit.value == 'maxLimit') {                    //Если достигнут максимальный лимит -> возращаемся к первому слайду
    currentSlide.value = Math.ceil(maxScroll.value)
  } else {
    currentSlide.value = -Math.ceil(maxScroll.value)              //Если достигнут минимальный лимин => возращаемся к последнему слайду
  }

}

const sliderStyleMove = computed(() => {                                  //Стили смены слайда
  return 'transform: translateX(' + sliderPosition.value + 'px)'
})

const sliderPosition = computed(() => {                                       //Текущая позиция слайдера
  return currentSlide.value * scrollSize.value - startPosition.value
})

const scrollSize = computed(() => {                                               //На какое расстояние нужно перемещать слайд
  return props.slideSize + MARGIN
})

const maxSlides = computed(() => {                                              //Максимальное количество слайдов, которые помещаются в обертку
  return props.sliderWrapperSize / (props.slideSize + MARGIN);
})

const slidesOver = computed(() => {                                             //Количество слайдов не помещающихся в обертку
  return props.listLength - maxSlides.value;
})

const startPosition = computed(() => {                                           //Отцентровка слайдера
  return (props.slideSize + MARGIN) * slidesOver.value / 2;
})

const maxScroll = computed(() => {                                               //Сколько раз можно вращать слайдер
  return slidesOver.value / 2;
})

const sliderLimit = computed(() => {                                            //Вычисление лимитов слайдера
  if(currentSlide.value <= -maxScroll.value && currentSide.value < 0) {
    return 'maxLimit';
  }
  else if(currentSlide.value >= maxScroll.value && currentSide.value > 0) {
    return 'minLimit';
  }
  else {
    return 'noLimit';
  }
})

</script>

<style media="screen" scoped>
  ul {
    transition: .5s all ease-out;
  }
</style>
