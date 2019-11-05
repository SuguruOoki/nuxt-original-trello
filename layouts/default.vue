<template>
  <div>
    <Header/>
    <nuxt/>
    <Footer/>
  </div>
</template>
<script>
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'
export default {
  components: {
    Header,
    Footer
  }
}
</script>

<style lang="scss">
$global-font: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
  Roboto, 'Helvetica Neue', Arial, sans-serif;

$default-font-size: 16px;
$default-font-color: #ffffff;

html {
  color: $default-font-color;
  font-family: $global-font;
  font-size: $default-font-size;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  body {
    background-color: #0079bf;
  }
}
</style>
