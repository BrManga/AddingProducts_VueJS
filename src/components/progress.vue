<template>
  <div v-if="productNumber>0" class="progress">
    <div
      class="progress-bar bg-info"
      role="progressbar"
      :style="{width: productNumber*10+'%'}"
      aria-valuenow="50"
      aria-valuemin="0"
      aria-valuemax="100"
    >{{productNumber}}/10</div>
  </div>
</template>
<script>
import { eventBus } from "../main";
export default {
  data: function() {
    return {
      productNumber: 0
    };
  },
  created() {
    eventBus.$on("productNumber", data => {
      this.productNumber = data;
    });
  }
};
</script>