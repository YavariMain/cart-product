<template>
  <div class="container-xl">
    <div class="row">
      <div class="col-xl-12">
        <b-img
          class="w-100"
          src="https://picsum.photos/1024/400/?image=41"
          fluid
          alt="Responsive image"
        ></b-img>
      </div>
    </div>
    <div class="row pt-5">
      <div class="col-xl-12">
        <h3>title</h3>
      </div>
    </div>
    <div class="row pt-3">
      <div class="col-xl-12">
        <p>
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
      </div>
    </div>
    <div class="row pt-3">
      <div class="col-xl-12">
        <b-button href="#" variant="primary">add to cart</b-button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        list:[],
      }
    },
    mounted() {
      this.getData()
    },
    methods:{
      getData(){
        this.$axios.get('/en/apiv2/catalog/get-product-list?slug=manufacturing-processing-machinery&page=1')
          .then(resp=>{
            this.list = resp.data.data.data;
            console.log(this.list)
          })
      }
    }
  }
</script>
