<template lang="html">
  <div class="footer__wrapper container">

    <a class="footer__logo logo" href="#">
      <img src="../../assets/images/logo-icon.png" alt="logo-icon">
      <span class="logo__caption">Enver</span>
    </a>

    <nav class="footer__nav">
      <ul class="footer__list">
        <li :class="['footer__item', {'footer__item_last': index == 2}]" v-for="(item, index) in footerList" :key="index">
          <a class="footer__link nav-link" href="#">{{ item }}</a>
        </li>
      </ul>
    </nav>

    <span class="footer__company">© 2020 Enver, All Rights Reserved</span>

  </div>
</template>

<script setup>
const footerList = [
  'Support',
  'Privacy Policy',
  'Terms and Conditions'
]
</script>
