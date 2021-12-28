<template>
  <div class="card shadow">
    <div v-for="product in products" :key="product.id">
      <Product 
        @delete="deleteProduct"
        :product="product"
      > 
      </Product>
      <hr />
    </div>

    <Footer :total="total" />
  </div>
</template>

<script>
import Product from "./Product.vue";
import Footer from "./Footer.vue";

export default {
  components: {
    Product,
    Footer,
  },

  props: {
    products: {
      type: Array,
      default: () => [],
    },
  },

  computed: {
    total() {
      return this.products.reduce((total, item) => {
        total += item.qtd * item.amount;
        return total;
      }, 0);
    },
  },

  methods: {
    deleteProduct(product) {
      this.$emit('delete', product);
    }
  },
};
</script>