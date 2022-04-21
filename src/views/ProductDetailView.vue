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
        <ControlCart :product-detail="productDetail"></ControlCart>
      </div>
    </div>
    <div class="row">
      <Product v-for="product in relatedProducts" :key="product.id" :product-detail="product"></Product>

    </div>
  </div>
</template>

<script>
import Rating from "@/components/Rating";
import ControlCart from "@/components/ControlCart";
import Product from "@/components/Product";
export default {
  name:"ProductDetailView",
  components: {Product, ControlCart, Rating},
  data() {
    return {
      productDetail: null,
      relatedProducts :[]
    }
  },
  mounted() {
    let currentId=this.$route.params.id
    fetch('https://fakestoreapi.com/products/'+currentId)
        .then(res=>res.json())
        .then(json=> {
          console.log(json)
          this.productDetail = json

          fetch('https://fakestoreapi.com/products/category/'+json.category)
          .then(res=>res.json())
          .then(json=>{
            this.relatedProducts=json.filter((el,index)=>el.id !=currentId).filter((el,index)=>index<4)
          })
        })
  }
}
</script>

<style scoped>

</style>