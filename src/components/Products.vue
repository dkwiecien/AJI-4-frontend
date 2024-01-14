<template>
  <div class="container" id="products-div">
    <div style="text-align: left">
      <h3>Filter products</h3>
      <br>
      <form>
        <div class="mb-3">
          <label class="form-label">Product Name</label>
          <input type="text" class="form-control" v-model="inputName"
                 placeholder="type your product name here!">
        </div>
        <div class="mb-3">
          <label class="form-label">Category Name</label>
          <input type="email" class="form-control" v-model="inputCategory"
                 placeholder="type your products category name here!">
        </div>
        <button type="button" class="btn btn-outline-secondary submit-btn">SEARCH</button>
      </form>
      <br>
    </div>
    <div style="text-align: left">
      <h3>Products</h3>
    </div>
    <br>
    <table class="table">
      <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Description</th>
        <th scope="col">Price</th>
        <th scope="col"></th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="product in filteredProducts" v-bind:key="product.name">
        <td>{{ product.name }}</td>
        <td>{{ product.description }}</td>
        <td>{{ product.price }}</td>
        <td>
          <button type="button" class="btn btn-secondary btn-sm" @click="addToList(product)">ADD</button>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
  <OrderComponent :orderedProducts="orderedProducts"/>
</template>

<script>
import OrderComponent from './Order.vue'
import axios from 'axios';
import _ from 'underscore';

export default {
  name: 'ProductsComponent',
  props: {},
  components: {
    OrderComponent
  },
  data: function () {
    return {
      products: [],
      orderedProducts: [],
      inputName: '',
      inputCategory: '',
      filteredProducts: this.products
    }
  },
  mounted: function () {
    var self = this;
    axios
        .get('http://127.0.0.1:8080/products')
        .then(res => {
          self.products = res.data;
          self.filteredProducts = res.data;
        });
  },
  methods: {
    addToList(product) {
      this.orderedProducts.push(product);
    },
    searchProducts() {
      this.filteredProducts = this.products;
      if (this.inputName != '') {
        this.filteredProducts = _.filter(this.filteredProducts, (product) => product.name.toLowerCase().includes(this.inputName.toLowerCase().trim()))
      }
      if (this.inputCategory != '') {
        this.filteredProducts = _.filter(this.filteredProducts, (product) => product.category.toLowerCase().includes(this.inputCategory.toLowerCase().trim()))
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
