<template>
  <div>
    <OptionsComponent/>
    <ProductsComponent/>
  </div>
</template>

<script>
import ProductsComponent from "@/components/Products.vue";
import OptionsComponent from "@/components/Options.vue";

export default {
  name: 'App',
  components: {
    OptionsComponent,
    ProductsComponent
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

body {
  background: #EEEEEE;
  margin-bottom: 8vh;
}

#options {
  background: darkgrey;
  overflow: hidden;
  position: fixed;
  top: 0;
  width: 100%;
}

#orders-div {
  margin-top: 15vh;
}

#products-div {
  margin-top: 15vh;
}

.nav-link {
  color: black;
}

.submit-btn {
  width: 10vw;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
