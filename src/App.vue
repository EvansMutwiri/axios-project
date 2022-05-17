<script setup>
  import { ref } from '@vue/reactivity';
import { onMounted } from '@vue/runtime-core';
  import axios from 'axios';

  const quote = ref('')

  const loadQ = async () => {
    try {
      const response = axios.get('https://api.kanye.rest/')
      quote.value = (await response).data.quote
    } catch (err) {
      console.log(err)
    }
  }

  onMounted(loadQ())

</script>

<template>
  <div>
    <h1 class="text-3xl text-yellow-100 leading-tight">"{{quote}}"</h1> <br>
    <p class="sm:text-center text-right text-white lg:mr-10">- Kanye West</p>
  </div>
</template>

<style>
@import './assets/base.css';
@import './assets/tailwind.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
  }

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
    background: linear-gradient(0deg rgba(34, 34, 34 / 54%),rgba(40, 40, 40 / 69%)), url('https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fksassets.timeincuk.net%2Fwp%2Fuploads%2Fsites%2F46%2F2016%2F09%2Fkanye-west.jpg&f=1&nofb=1') no-repeat  center;
    background-size: cover;

  }

  #app {
    display: grid;
    grid-template-columns: 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
