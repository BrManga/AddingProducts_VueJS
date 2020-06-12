<template>
  <div class="container">
    <h1 class="text-center">Adding Products</h1>
    <hr />
    <newProduct></newProduct>
    <br />
    <br />
    <appProgress></appProgress>
    <br />
    <br />

    <products></products>
  </div>
</template>

<script>
import Products from "./components/products";
import newProduct from "./components/newProduct";
import Progress from "./components/progress";
export default {
  components: {
    products: Products,
    newProduct: newProduct,
    appProgress: Progress
  }
};
</script>

<style>
body {
  background-color: aliceblue;
  padding-top: 20px;
  padding-bottom: 20px;
}

.card {
  margin-right: 5px;
  margin-bottom: 5px;
}

.card:last-child {
  margin-right: 0px;
}

.col-md-2 {
  max-width: 15.666667% !important;
}

.product-container {
  margin-left: 15px;
}
</style>

