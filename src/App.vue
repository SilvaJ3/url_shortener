<template>
  <div id="app" class="h-full w-full">
    <Header />
    <Banner />
    <SectionURL />
    <SectionBoost />
    <TheFooter />
  </div>
</template>

<script>
import Header from "./components/Header"
import Banner from "./components/Banner"
import SectionURL from "./components/SectionURL"
import SectionBoost from "./components/SectionBoost"
import TheFooter from "./components/TheFooter"

export default {
  name: 'App',
  components: {
    Header,
    Banner,
    SectionURL,
    SectionBoost,
    TheFooter
  }
}
</script>

<style>
#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.button {
  background-color: #2bd1d1;
}
</style>
