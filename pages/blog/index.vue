<template>
  <section class="se-product">
    <div class="container-xl">
      <div class="row">
        <div class="col-xl-12">
          <h2>products cat title</h2>
        </div>
        <div class="col-xl-4" v-for="item in list">
          <template>
            <b-card
              :title="item.location"
              :img-src="item.image"
              img-alt="Image"
              img-top
              tag="article"
              class="mb-2"
            >
              <b-card-text>
                Some quick example text to build on the card title and make up
                the bulk of the card's content.
              </b-card-text>
              <div class="d-flex">
                <b-button href="#" variant="primary">add to cart</b-button>
                <NuxtLink
                  :to="`/blog/${item.slug}`"
                  style="margin-left: 5px"
                >more</NuxtLink
                >
              </div>
            </b-card>
          </template>
        </div>
      </div>
    </div>
  </section>
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
