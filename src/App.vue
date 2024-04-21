<script setup lang="ts">
import VueQrcode from '@chenfengyuan/vue-qrcode';
import { ref } from 'vue';
const qrcodeUri = ref('');
setInterval(() => {
  if (location.href.includes('#')) {
    qrcodeUri.value = decodeURIComponent(location.href.split('#')[1]);
  }
}, 100);
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="64" height="64" />
    <div class="wrapper">
      <div class="greetings">
        <h3>
          {{ 'This page is only for easy to transform text to qrcode'.toLocaleUpperCase() }}
        </h3>
      </div>
    </div>
  </header>

  <main style="display: flex; justify-content: center; align-items: center;">
    <vue-qrcode v-if="qrcodeUri" class="qrcode" :value="qrcodeUri" :options="{ width: 200 }"></vue-qrcode>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
