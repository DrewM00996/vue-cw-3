<template>
  <div>
  <div class="checkout-header">
    <h2>Cart <span class="cart-count">{{ this.cart.length }} items</span></h2>
  </div>
  <div class="page-container-checkout">
      <div class="cart-section">
        <div class="card mb-3" style="max-width: 540px;" v-for='product in cart' :key="product.id">
            <div class="row g-0">
                <div class="col-md-4">
                    <img v-bind:src="product.image" class="img-fluid rounded-start" alt="product">
                </div>
                <div class="col-md-8">
                    <div class="card-body">
                        <input type="hidden" v-text="product.id">
                        <h5 v-text="product.title"></h5>
                        <p>Price: £ {{ product.price }}</p>
                        <button class="btn btn-dark"  @click="cart.splice(index,1)">
                            Remove
                        </button>
                    </div>
                </div>
            </div>
        </div>
      </div>
      <div class="checkout-section">
        <div class="checkout-form">
            <div class="mb-3">
                <label class="form-label">Name</label>
                <input type="text" class="form-control" id="nameInput" v-model="name">
            </div>
            <div class="mb-3">
                <label class="form-label">Address</label>
                <input type="text" class="form-control" id="addressInput" v-model="address">
            </div>
            <button type="submit" class="btn btn-primary confirm-checkout-btn" @click = 'confirmCheckout(cart)'>Checkout</button>
        </div>
      </div>
  </div>






</div>
</template>

<script>
export default {
  name: "CheckoutSection",
  props: ['cart'],
  data() {
    return {
      name: "",
      address: "",
    };
  },
  methods: {
      confirmCheckout(cart) {
          this.name = ''
          this. address = ''
          alert("Your order has been placed. Thank you for shopping") 
          this.$emit('checkout',cart);

      }
  }
  
};
</script>

<style scoped>
.checkout-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    margin-bottom: 50px;
    border-bottom: 3px solid slategray;
}

.cart-count {
  font-size: 16px;
  color: slategray;
}

.page-container-checkout {
  display: grid;
  grid-template-columns: 5fr 3fr;
}

.checkout-form {
  background: white;
  padding: 30px;
}
</style>