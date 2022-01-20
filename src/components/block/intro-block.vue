<template lang="html">
  <section class="intro container">

    <div class="intro__main">

      <h2 class="intro__title title">Build Your Awesome Platform</h2>

      <p class="intro__subtitle subtitle">
        Enver studio is a digital studio that offers several services such as UI/UX Design to developers,
        we will provide the best service for those of you who use our services.
      </p>

      <a class="intro__link" href="#">
        <span>Our services</span>
        <moreIcon />
      </a>

    </div>

    <div class="intro__image-wrapper">
      <img class="intro__image" src="../../assets/images/intro-image-main.png" alt="person-image">
      <zigzagIcon class="intro__zigzag icon-zigzag" />
      <circleIcon class="intro__circle icon-circle" />
      <plusIcon class="intro__plus icon-plus" />
      <triangleIcon class="intro__triangle icon-triangle" />
    </div>

  </section>
</template>

<script setup>
import moreIcon from '../icons/more-icon'
import circleIcon from '../icons/circle-icon'
import plusIcon from '../icons/plus-icon'
import zigzagIcon from '../icons/zigzag-icon'
import triangleIcon from '../icons/triangle-icon'
</script>

<style lang="css" scoped>
</style>
