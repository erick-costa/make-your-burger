<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <RouterView />
  <Footer />
</template>

<script>
import { RouterView } from "vue-router"
import Footer from "./components/Footer.vue"
import Navbar from "./components/Navbar.vue"
export default {
  name: "App",
  components: { Navbar, Footer },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burger",
    }
  },
}
</script>

<style>
* {
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body,
html {
  min-height: 100%;
  height: 100%;
}

#app {
  min-height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>
