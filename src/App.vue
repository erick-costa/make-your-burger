<script>
import { RouterView } from "vue-router"
import Footer from "./components/Footer.vue"
import Navbar from "./components/Navbar.vue"
export default {
  name: "App",
  components: { Navbar, Footer },
}
</script>

<template>
  <Navbar />
  <RouterView />
  <Footer />
</template>

<style></style>
