<template>
  <div class="container" v-if="productDetail">
    <div class="row justify-content-center">
      <div class="col-lg-3 ">
        <img :src="productDetail.image" class="w-100" alt="">
      </div>
      <div class="col-lg-5 ">
        <div class="">
          <h4>{{productDetail.title}}</h4>
          <div class="d-flex justify-content-between my-4">
            <p class="mb-0 badge bg-danger ">{{productDetail.category}}</p>
            <Rating :rating="productDetail.rating"></Rating>
          </div>
          <div class="">
            <p class="mb-0 ">{{productDetail.description}}</p>
          </div>
        </div>
      </div>
      <div class="col-8 my-5">
        <ControlCart></ControlCart>
      </div>
    </div>
  </div>
</template>

<script>
import Rating from "@/components/Rating";
import ControlCart from "@/components/ControlCart";
export default {
  name:"ProductDetailView",
  components: {ControlCart, Rating},
  data() {
    return {
      productDetail: null
    }
  },
  mounted() {
    fetch('https://fakestoreapi.com/products/'+this.$route.params.id)
        .then(res=>res.json())
        .then(json=> {
          console.log(json)
          this.productDetail = json
        })
  }
}
</script>

<style scoped>

</style>