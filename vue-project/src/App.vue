<template>
        <!-- Navigation-->
        <nav class="navbar navbar-expand-lg">
            <div class="container px-4 px-lg-5">
                <a class="navbar-brand" href="#">✦✦✦</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"><span class="navbar-toggler-icon"></span></button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0 ms-lg-4">
                        <li class="nav-item">
                          <router-link class="nav-link active" aria-current="page" to="/">home</router-link>
                        </li>
                        <li class="nav-item">
                          <router-link class="nav-link" :to="{name: 'about'}">about</router-link>
                        </li>
                        <li class="nav-item">
                          <router-link class="nav-link" to="/new-product">new product</router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
        <!-- Header-->
        <header class="">
            <img src="https://www.nicepng.com/png/full/1-17987_bubbles-png.png" class="header-img">
        </header>
        <Router-view
        :inventory = "inventory"
        :addInv = "addInventory"
        :removeInv = "removeInventory"
        :updateInv = "updateInventory"
        />
</template>

<script>
// import inventory from '@/product.json'
import ProductDataService from '@/services/ProductDataService'

export default {
  data: () => {
    return {
      inventory: []
    }
  },
  methods: {
    addInventory (product) {
      this.inventory.push(product)
    },
    removeInventory (index) {
      this.inventory.splice(index, 1)
    },
    updateInventory (index, data) {
      this.inventory[index].name = data.name
      this.inventory[index].photo = data.photo
      this.inventory[index].price = data.price
      this.inventory[index].description = data.description
      this.inventory[index].type = data.type
    }
  },
  mounted () {
    ProductDataService.getAll()
      .then(response => {
        this.inventory = response.data
      })
  }
}
</script>
