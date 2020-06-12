<template>
  <div>
    <h3 v-if="productList.length>0" class="text-center">
      List of Added Products
      <hr />
    </h3>

    <div class="row product-container">
      <productPage v-for="(product,index) in productList" :key="index">
        <img class="card-img-top" :src="product.selectedImage" alt="Card image cap" />
        <div class="card-body">
          <h5 class="card-title">{{product.title}}</h5>
          <small>
            <strong>Count :</strong>
            {{product.count}}
          </small>
          <br />
          <small>
            <strong>Price :</strong>
            {{product.price}}
          </small>
          <br />
          <small>
            <strong>Total:</strong>
            {{product.totalPrice}}
          </small>
        </div>
      </productPage>
    </div>
  </div>
</template>
<script>
import Product from "./product";
import { eventBus } from "../main";
export default {
  components: {
    productPage: Product
  },
  data: function() {
    return {
      productList: []
    };
  },
  created() {
    eventBus.$on("product", data => {
      if (this.productList.length < 10) {
        this.productList.push(data);
        eventBus.$emit("productNumber", this.productList.length);
      } else {
        alert("It is enough, just 10 items");
      }
    });
  }
};
</script>