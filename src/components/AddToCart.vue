<template>
  <div>
    <button v-if="isAdded" class="btn btn-outline-primary active w-100" @click.stop>Added</button>
    <button v-else class="btn btn-outline-primary w-100" @click.stop="add">Add to cart</button>

  </div>
</template>

<script>
export default {
  name:"AddToCartButton",
  data() {
    return {
      isAdded: false
    }
  },
  methods: {
    add() {
      this.isAdded=true
    }
  },
}
</script>

<style scoped>

</style>