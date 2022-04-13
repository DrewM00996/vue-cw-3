<template>
  <div>
    <div class="card" style="width: 18rem;" v-for="product in products" :key="product.id">
      <img v-bind:src="product.image" class="card-img-top">
      <div class="card-body">
        <h5 v-html="product.title"></h5>
        <p v-text="product.location"></p> 
        <p> Available stock:  {{product.availableSpace}}</p> 
        <button class="btn btn-dark" @click="add(product)">Add to cart</button>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "ProductList",

  data() {
    return {
      products: [
        {
          id: 1001,
          title: "Book Club",
          location: "London",
          price: 25,
          availableSpace: 5,
          image: "bookclub.jpg",
          rating: 3,
        },
        {
          id: 1002,
          title: "Rugby Club",
          location: "Belsize Park",
          price: 75,
          availableSpace: 5,
          image: "rugbyclub.jpg",
          rating: 4,
        },
        {
          id: 1003,
          title: "Music Club",
          location: "Birmingham",
          price: 100,
          availableSpace: 5,
          image: "guitarclub.jpg",
          rating: 4,
        },
        {
          id: 1004,
          title: "Cheerleading Club",
          location: "Poynton",
          price: 80,
          availableSpace: 5,
          image: "cheerleadingclub.jpg",
          rating: 3,
        },
        {
          id: 1005,
          title: "Artifical Intelligence Club",
          location: "Yorkshire",
          price: 50,
          availableSpace: 5,
          image: "aiclub.jpg",
          rating: 1,
        },
        {
          id: 1006,
          title: "Esports Club",
          location: "Uxbridge",
          price: 100,
          availableSpace: 5,
          image: "esportsclub.png",
          rating: 5,
        },
        {
          id: 1007,
          title: "Model U.N Club",
          location: "London",
          price: 50,
          availableSpace: 5,
          image: "modelunclub.jpg",
          rating: 2,
        },
        {
          id: 1008,
          title: "Film Club",
          location: "Leeds",
          price: 150,
          availableSpace: 5,
          image: "filmclub.png",
          rating: 4,
        },
        {
          id: 1009,
          title: "Rock Climbing Club",
          location: "Surrey",
          price: 200,
          availableSpace: 5,
          image: "rockclimbingclub.jpg",
          rating: 5,
        },
        {
          id: 10010,
          title: "Football Club",
          location: "Merseyside",
          price: 70,
          availableSpace: 5,
          image: "footballclub.jpg",
          rating: 5,
        },
      ],
    };
  },
  methods: {
    add(product) {
      console.log("added product", product.id);
      this.$emit('addProduct',product);
    },
  }
  
};
</script>

