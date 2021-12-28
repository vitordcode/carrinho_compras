<template>
  <div class="container mt-5">
    <h2 class="text-center mb-5">Carrinho de compra</h2>

    <Cart 
      @delete="deleteProduct"
      :products="products">
    </Cart>
  </div>
</template>

<script>
import Cart from "./components/Cart.vue";

export default {
  name: "App",
  components: {
    Cart,
  },

  data() {
    return {
      products: [
        { id: 1, name: 'Produto A', amount: 10.50, qtd: 1 },
        { id: 2, name: 'Produto B', amount: 5, qtd: 1 },
        { id: 3, name: 'Produto C', amount: 7, qtd: 1 },
      ]
    }
  },

  methods: {
    deleteProduct(product) {
      const index = this.products.findIndex(o => o.id === product.id)
      if (index >= 0 ) {
        this.products.splice(index, 1);
      }
    },
  }
};
</script>