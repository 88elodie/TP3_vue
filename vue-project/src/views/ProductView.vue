<template>
    <div class="food">
      <section class="py-5">
          <div class="container px-4 px-lg-5 my-5">
              <div class="row gx-4 gx-lg-5 align-items-center">
                  <div class="col-md-6"><img class="card-img-top mb-5 mb-md-0" :src="require(`@/assets/img/600/${product.photo}`)" :alt="product.name" /></div>
                  <div class="col-md-6">
                      <h1 class="display-5 fw-bolder">{{ product.name }}</h1>
                      <div class="fs-5 mb-3">
                          <span class="text-decoration-line-through"></span>
                          <span>$ {{ product.price.toFixed(2) }}</span>
                      </div>
                      <p class="lead">Description :</p>
                      <p>{{ product.description }}</p>
                       <router-link class="btn btn-secondary mt-3"  :to="{name: 'edit-product', params: {id: product.id} }">Edit</router-link>
                  </div>
              </div>
          </div>
      </section>
    </div>
</template>

<script>
export default {
  props: ['inventory', 'addTo'],
  computed: {
    product () {
      const product = this.inventory.find((p) => {
        return p.name === this.$route.params.id
      })
      return product
    },
    productIndex () {
      const index = this.inventory.findIndex((p) => {
        return p.name === this.$route.params.id
      })
      return index
    }
  }
}
</script>
