<template>
  <div class="border border-primary rounded p-3">
    <div class="row ">
      <div class="col-8"></div>
      <div class="col-4">
        <div class="row mb-3 g-2">
          <div class="col-3">
            <button class="btn btn-primary w-100" @click="minus">
              <i class="fa-solid fa-minus"></i>
            </button>
          </div>
         <div class="col-6">
           <input type="text" v-model="quantity" class="form-control text-center">
         </div>
          <div class="col-3">
            <button class="btn btn-primary w-100" @click="plus">
              <i class="fa-solid fa-plus"></i>
            </button>
          </div>

        </div>
        <AddToCartButton></AddToCartButton>
      </div>
    </div>

  </div>
</template>

<script>
import AddToCartButton from "@/components/AddToCart";
export default {
  name:"ControlCart",
  data() {
    return {
      quantity: 1
    }
  },
  methods: {
    plus() {
      this.quantity++
    },
    minus(){
      if(this.quantity>1){
        this.quantity--
      }
    }

  },
  components: {AddToCartButton}
}
</script>

<style scoped>

</style>