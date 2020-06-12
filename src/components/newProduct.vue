<template>
  <div class="row">
    <div class="card offset-2 col-md-3">
      <div class="card-body tex-center d-flex align-items-center flex-column">
        <img
          height="128"
          class="img-responsive text-center mb-3"
          :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage"
        />
        <input
          ref="file"
          type="file"
          style="display: none;"
          @change="onChange($event)"
          class="form-control"
        />
        <button
          class="btn btn-outline-secondary"
          type="button"
          @click="$refs.file.click()"
        >Select Photo</button>
      </div>
    </div>
    <div class="col-md-5">
      <div class="col-md-11 card">
        <div class="card-body">
          <div class="form-group">
            <label>Item Name</label>
            <input
              type="text"
              v-model="product.title"
              class="form-control"
              placeholder="Enter Item Name"
            />
          </div>
          <div class="row">
            <div class="form-group col-md-6">
              <label>Item Number</label>
              <input
                type="text"
                v-model="product.count"
                class="form-control"
                placeholder="Enter Item Number"
              />
            </div>
            <div class="form-group col-md-6">
              <label>Item Price</label>
              <input
                type="text"
                v-model="product.price"
                class="form-control"
                placeholder="Enter Price"
              />
            </div>
          </div>
          <button @click="addProduct" class="btn btn-outline-info btn-block">Ekle!</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { eventBus } from "../main";
export default {
  data: function() {
    return {
      product: {},
      product: {
        title: null,
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null
      }
    };
  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);
    },
    addProduct() {
      this.product.totalPrice = this.product.price * this.product.count;
      eventBus.$emit("product", this.product);
      this.product = {
        title: null,
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null
      };
    }
  }
};
</script>