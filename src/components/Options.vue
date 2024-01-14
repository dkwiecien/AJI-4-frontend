<template>
  <div id="options">
    <ul class="nav justify-content-end">
      <li class="nav-item">
        <a class="nav-link active" aria-current="page" @click="viewOrderPage">
          <img src="../assets/koszyk.png" width="20">
        </a>
      </li>
      <li class="nav-item">
        <a class="nav-link" @click="viewProductsPage">Menu</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'OptionsComponent',
  props: {},
  data: function () {
    return {}
  },
  methods: {
    viewOrderPage() {
      let productsDiv = document.getElementById('products-div');
      let ordersDiv = document.getElementById('orders-div');
      ordersDiv.style.display = 'block';
      productsDiv.style.display = 'none';
    },
    viewProductsPage() {
      let productsDiv = document.getElementById('products-div');
      let ordersDiv = document.getElementById('orders-div');
      ordersDiv.style.display = 'none';
      productsDiv.style.display = 'block';
    }
  }
}


</script>


<style scoped>

</style>