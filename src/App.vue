<template>

  <header class="main-header">
    <headerBlock />
  </header>

  <introBlock />

  <ourPlusesBlock />

  <servicesBlock />

  <portfolioBlock />

  <contactBlock />

  <footer class="main-footer">
    <footerBlock />
  </footer>

</template>

<script setup>
import headerBlock from './components/block/header-block'
import introBlock from './components/block/intro-block'
import ourPlusesBlock from './components/block/our-pluses-block'
import servicesBlock from './components/block/services-block'
import portfolioBlock from './components/block/portfolio-block'
import contactBlock from './components/block/contact-block'
import footerBlock from './components/block/footer-block'
</script>

<style src="./assets/styles/mobile.css"></style>
<style src="./assets/styles/mobile-small.css"></style>
<style src="./assets/styles/middle.css"></style>
<style src="./assets/styles/desktop.css"></style>
