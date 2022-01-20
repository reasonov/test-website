<template lang="html">
  <div class="main-header__wrapper container">

    <a class="main-header__logo logo" href="#">
      <img class="logo__image" src="../../assets/images/logo-icon.png" alt="logo-icon">
      <span class="logo__caption">Enver</span>
    </a>

    <transition name="menuAm">
      <nav class="main-header__nav main-nav" v-show="menuState">
        <ul class="main-nav__list">
          <li class="main-nav__item" v-for="(item, index) in headerList" :key="index">
            <a class="main-nav__link nav-link" href="#">{{ item }}</a>
          </li>
        </ul>
      </nav>
    </transition>

    <button class="main-header__request" type="button" name="button">Contact us</button>

    <button class="menu-toggler" type="button" name="button" @click="menuToggle">
      <div class="menu-toggler__wrapper">
        <span class="menu-toggler__line menu-toggler__line1"></span>
        <span class="menu-toggler__line menu-toggler__line2"></span>
        <span class="menu-toggler__line menu-toggler__line3"></span>
      </div>
    </button>

  </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'

const headerList = [
  'Home',
  'Services',
  'Our project',
  'About us'
]

const menuState = ref(false)

function menuToggle() {
  menuState.value = !menuState.value
}

const windowWidth = ref(0)

watch(windowWidth, () => {
  if(windowWidth.value >= 1420) {
    menuState.value = true
  } else {
    menuState.value = false
  }
})

function resizeWindow() {
  windowWidth.value = document.documentElement.clientWidth
}

onMounted(() => {
  resizeWindow()
  window.addEventListener('resize', resizeWindow)
})

// beforeUnmount(() => {
//   window.removeEventListener('resize', resizeWindow)
// })

</script>

<style media="screen">
  .menuAm-enter-active {
    overflow: hidden;
    animation: .5s menuOpen ease-out;
  }

  .menuAm-leave-active {
    overflow: hidden;
    animation: .5s menuClose ease-out;
  }

  @keyframes menuOpen {
    0% {
      height: 0vh;
    }

    100% {
      height: 100vh;
    }
  }

  @keyframes menuClose {
    0% {
      height: 100vh;
    }

    100% {
      height: 0vh;
    }
  }
</style>
