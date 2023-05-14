<template>
  <div>
    <ul>
      <li v-for="product in filteredProducts" :key="product.id">
        <div class="product">
          <div class="image">
            <img
              class="image-product"
              :src="product.image"
              :alt="product.title"
            />
          </div>

          <div class="detail-product">
            <h2 class="title-product">{{ product.title }}</h2>
            <div class="review">
              <p class="category">{{ product.category }}</p>
              <p class="rating">{{ product.rating.rate }}/5</p>
            </div>
            <hr />
            <p class="description">{{ product.description }}</p>
            <hr />
            <h3 class="price">${{ product.price }}</h3>
            <div class="button">
              <button class="buy-btn">Buy Now</button>
              <button
                class="next-btn"
                v-if="index >= 0"
                @click="previousProduct()"
              >
                Previous Product
              </button>
              <button
                class="next-btn"
                v-if="index < products.length - 1"
                @click="nextProduct()"
              >
                Next Product
              </button>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  // name: "ProductList",
  data() {
    return {
      products: [],
      prodcut: {},
      index: 0,
    };
  },
  async created() {
    const response = await fetch("https://fakestoreapi.com/products");
    const data = await response.json();
    this.products = data;
    this.prodcut = this.products[this.index];

    // fetch("https://fakestoreapi.com/products/category/men's clothing")
    //   .then((response) => response.json())
    //   .then((data) => {
    //     this.products = data;
    //     this.product = this.products[this.index];
    //   });
  },
  computed: {
    filteredProducts() {
      return this.products.filter((product) => {
        return (
          product.category === "men's clothing" ||
          product.category === "women's clothing"
        );
      });
    },
  },
  methods: {
    nextProduct() {
      this.index++;
      this.product = this.products[this.index];
    },
    previousProduct() {
      this.index--;
      this.product = this.products[this.index];
    },
  },
};
</script>
