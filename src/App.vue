<template>
  <div id="app">
    <license></license>
  </div>
</template>

<script>
import License from "@/components/License";

export default {
  name: 'App',
  components: {
    License
  }
}
</script>

<style lang="scss">

@font-face {
  font-family: "BebasNeue-Regular";
  src: url("./assets/fonts/BebasNeue-Regular.woff") format("woff"), /* Modern Browsers */
  url("./assets/fonts/BebasNeue-Regular.woff2") format("woff2"); /* Modern Browsers */
  font-weight: normal;
  font-style: normal;
}

#app {
  font-family: BebasNeue-Regular, sans-serif;
}
</style>
