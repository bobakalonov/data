<template>
  <div class="home">
    <router-link class="cart" :to="{ name: 'cart' }">Cart:({{ cart.length }})</router-link>
    <product-card
      v-for="(product) in products"
      :key="product.id"
      :product="product"
      @update-cart="incCart"
    />
  </div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'
export default {
  name: "HomeView",
  data() {
    return {
      cart: [],
      products: [
        {
          id: "prp01",
          brand: "Iphone",
          model: "13 Pro Max",
          image: "img/01.webp",
          desc: "Iphone image",
          inStock: true,
          details: ["Camera: 12px", "Battery: 4000mAh", "Corpus: Aluminium"],
          quantity:0,
          variants: [
            {
              id: "va01",
              color: "gold",
              image: "img/01.webp",
              quantity: 50,
            },
            {
              id: "va02",
              color: "green",
              image: "img/02.jpg",
              quantity: 0,
            },
          ],
        },
      ],
    };
  },
  components: { ProductCard },
  methods: {
    incCart(id) {
      this.cart.push(id);
    },
  },
};
</script>
