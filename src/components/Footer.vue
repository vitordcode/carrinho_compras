<template>
  <div class="card-footer d-flex align-items-center justify-content-between">
    <a href=""> Continuar comprando </a>

    <div>
      <small class="text-muted">Total:</small>
      <span class="fs-5">R${{ total }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    total: {
      type: Array,
      default: () => [],
    },
  },
}
</script>