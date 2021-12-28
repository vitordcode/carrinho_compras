<template>
  <div class="d-flex align-items-center m-3">
    <div class="d-flex align-items-center">
      <div class="me-3">
        <img
          src="https://via.placeholder.com/72"
          alt=""
          class="rounded-circle"
        />
      </div>

      <div class="ml-3">
        <h4 class="mb-0">{{ product.name }}</h4>
        <span class="text-muted fs-6">#{{ product.id }}</span>
      </div>
    </div>

    <div class="ms-auto d-flex align-items-center">
      <div class="d-flex align-items-center" style="width: 120px">
        <div class="input-group">
          <button
            @click="remove()"
            :disabled="product.qtd <= 1"
            class="btn btn-outline-secondary"
            type="button"
            id="button-addon1"
          >
            -
          </button>
          <input type="text" :value="product.qtd" readonly class="form-control text-center" />
          <button
            @click="add()"                     
            class="btn btn-outline-secondary"
            type="button"
            id="button-addon1"
          >
            +
          </button>
        </div>
      </div>

      <div class="d-flex align-items-center mx-4">R${{ total }}</div>

      <div class="d-flex align-items-center">
        <button
          @click="deleteProduct()"
          class="btn btn-sm btn-outline-danger">
          <svg
            style="width: 20px; height: 20px"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            ></path>
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
    
    }
  },

  props: {
    product: {
      type: Object,
      default: () => ({}),
    }
  },

  methods: {
    remove() {
      if (this.product.qtd <= 1) {
        return;
      }

      this.product.qtd--;
    },
    add() {
      this.product.qtd++;
    },

    deleteProduct() {
      this.$emit('delete', this.product)
    }
  },

  computed: {
    total() {
      return this.product.amount * this.product.qtd;
    },
  },
}
</script>