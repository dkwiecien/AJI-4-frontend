<template>
  <div class="container" id="orders-div" style="display: none">
    <div style="text-align: left">
      <h3>Your Order</h3>
    </div>
    <table class="table table-bordered">
      <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Description</th>
        <th scope="col">Price</th>
        <th scope="col">Amount</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="product in displayOrderedProducts" v-bind:key="product.name">
        <td>{{ product.name }}</td>
        <td>{{ product.description }}</td>
        <td>{{ product.price }}</td>
        <td>{{ countProducts(product) }}</td>
      </tr>
      </tbody>
    </table>
    <div class="alert alert-dark" role="alert">
      Total Price: {{ calculateTotalPrice() }}
    </div>
    <div style="text-align: left">
      <button type="button" class="btn btn-outline-secondary submit-btn">PURCHASE</button>
    </div>
    <br>
    <br>
    <br>
    <div style="text-align: left">
      <h3>Contact</h3>
      <form>
        <div class="mb-3">
          <label class="form-label">Username</label>
          <input type="text" class="form-control" aria-describedby="emailHelp"
                 placeholder="type your username">
        </div>
        <div class="mb-3">
          <label class="form-label">Email address</label>
          <input type="email" class="form-control" aria-describedby="emailHelp"
                 placeholder="eg. email@gmail.com">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label class="form-label">Phone Number</label>
          <input type="text" class="form-control" placeholder="XXXXXXXXX">
        </div>
        <button type="button" class="btn btn-outline-secondary submit-btn">SUBMIT</button>
      </form>
    </div>

  </div>
</template>

<script>
import _ from 'underscore';

export default {
  name: 'OrderComponent',
  props: {
    orderedProducts: []
  },
  data: function () {
    return {
      countedProducts: []
    }
  },
  computed: {
    displayOrderedProducts() {
      return _.uniq(this.orderedProducts);
    }
  },
  methods: {
    countProducts(product) {
      return _.filter(this.orderedProducts, (p) => p.name.includes(product.name)).length;
    },
    calculateTotalPrice() {
      let totalprice = 0;
      this.orderedProducts.forEach((product) => {
        totalprice += product.price;
      })
      return totalprice;
    }
  }
}
</script>


<style scoped>

</style>