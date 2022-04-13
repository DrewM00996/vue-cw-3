<template>
  <div id="app">
    <header>
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container p-1">
            <a class="navbar-brand logo" href="#">{{ sitename }}</a>
            <div class="collapse navbar-collapse" id="navbarNav">
                <!-- Search Products -->
                <div class="d-flex ms-auto">
                    <input type="hidden" class="form-control me-2" placeholder="Search">
                </div>
                <!-- Checkout Button -->
                <button class="btn btn-primary checkout-btn" @click="showCheckout">
                  {{ this.cart.length }}
                  Checkout
                </button>
            </div>
        </div>
      </nav>
    </header>
    <main class="container">
      <div v-if="showProduct">
        <product-list class="products-section" @addProduct="addToCart"></product-list>
      </div>
      <div v-else>
        <checkout-section :cart="cart" @checkout="checkout"></checkout-section>
      </div>
    </main>
  </div>
</template>

<script>

// importing components
import productList from "./components/ProductList.vue";
import checkoutSection from "./components/CheckoutSection.vue";

export default {
  name: 'App',
  // registering components with app
  components: {
    productList,
    checkoutSection,
  },
  data() {
    return {
      sitename : 'Afterschool Activities',
      cart: [],
      showProduct: true,
    }
  },
  methods: {
    // Checks the showProduct value according to the state and return a value of true/false
    showCheckout() {this.showProduct = this.showProduct ? false : true;},
    addToCart(product) {
     console.log("addProduct event received by the root component.");
      this.cart.push(product);
    },
    checkout() {
     this.cart = [];
    },
  }
}
</script>

<style scoped>
  main {
    margin-top: 40px;
  }

  .products-section {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-column-gap: 10px;
    grid-row-gap: 18px;
  }
</style>
