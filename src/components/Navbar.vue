<template>
  <nav>
    <RouterLink to="/">
      <img src="" alt="logo" id="logo" />
    </RouterLink>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/orders">Pedidos</RouterLink>
  </nav>
</template>

<script>
import { RouterLink } from "vue-router"
export default {
  name: "Navbar",
}
</script>

<style scope></style>
