<template>
    <div>
        <div class="menu">
            <a v-for="a in 메뉴들" :key="a"></a>
        </div>
        <DiscountBanner />

        <ProductVeiw @openModal="modalPop = true; clickProduct = $event" :product="products[i]" v-for="(a, i) in products" :key="i" />

        <ModalYellow @closeModal="modalPop = false;" :products="products" :clickProduct="clickProduct" :modalPop="modalPop"/>
    </div>
</template>

<script>
import oneRoom from './data.js';
import DiscountBanner from './DiscountBanner.vue';
import ModalYellow from './ModalYellow.vue';
import ProductVeiw from './ProductVeiw.vue';

export default {
  name: 'App',
  data() {
    return {
        메뉴들: ["Home", "Shop", "About"],
        modalPop: false,
        // products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
        products: oneRoom,
        nums: 0,
        clickProduct: 0
    }
  },
  methods: {
    신고() {
       return this.num ++
    }
  },
  components: {
    DiscountBanner,
    ModalYellow,
    ProductVeiw
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
    margin: 0;
}
div {
    box-sizing: border-box;
}
.product-card {
    margin-bottom: 50px;
}
.product-card h4 {
    cursor: pointer;
}
.product-card h4:hover {
    color: green;
}
.product-card img {
  width: 500px;
}
.discount{
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
.black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    position:fixed;
    top: 0;
    left: 0;
    padding: 20px;
}
.white-bg {
    width: 40%;
    background: white;
    border-radius: 8px;
    padding: 20px;
    margin: 160px auto;
}
</style>
