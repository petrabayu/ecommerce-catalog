<template>
  <div>
    <product-list />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";

// export default {
//   name: "App",
//   // components: {
//   //   HelloWorld
//   // }
// };
import ProductList from "./components/ProdcutList.vue";

export default {
  name: "App",
  components: {
    ProductList,
  },
};
</script>

<style>
/* Import page.css */
@import url("assets/style/page.css");
</style>
