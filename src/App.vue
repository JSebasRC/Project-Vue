<template>
<Suspense>
  <template #default>
    <Home/>
  </template>
  <template #fallback>
    <splash-screen />
  </template>
</Suspense>
</template>

<script>
import { defineAsyncComponent } from '@vue/runtime-core';
import SplashScreen from './components/SplashScreen.vue';

export default {
  components: {
    SplashScreen,
    Home: defineAsyncComponent( () =>
     new Promise ((resolve) => {
      setTimeout(() =>{
        resolve(import("./components/Home.vue"))
      }, 2500);
     })
    )
  }

}
</script>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
