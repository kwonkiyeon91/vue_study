<template>
    <div>
        <div class="menu">
            <a v-for="a in 메뉴들" :key="a"></a>
        </div>
        <DiscountBanner :showDiscount="showDiscount" />

        <button @click="priceLowSort">가격 낮은순 정렬</button>
        <button @click="priceHighSort">가격 높은순 정렬</button>
        <button @click="titleSort">상품명 순 정렬</button>
        <button @click="sortBack">되돌리기</button>
        
        <ProductVeiw @openModal="modalPop = true; clickProduct = $event" :product="products[i]" v-for="(a, i) in products" :key="i" />

        <transition name="fade">
          <ModalYellow @closeModal="modalPop = false;" :products="products" :clickProduct="clickProduct" :modalPop="modalPop"/>
        </transition>
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
        showDiscount: 30,
        메뉴들: ["Home", "Shop", "About"],
        modalPop: false,
        // products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
        products: oneRoom,
        originProduct: [...oneRoom],
        nums: 0,
        clickProduct: 0
    }
  },
  methods: {
    increase() {
       return this.num ++
    },
    priceLowSort() {
     this.products.sort(function(a,b) {
      return a.price - b.price;
     })
    },
    priceHighSort() {
     this.products.sort(function(a,b) {
      return b.price - a.price;
     })
    },
    titleSort() {
     this.products.sort(function(a, b) {
      var aa = a.title.toUpperCase();
      var bb = b.title.toUpperCase();

      return aa > bb ? 1 : aa < bb ? -1 : 0;
     });
    },
     sortBack() {
    //  this.products.sort(function(a,b) {
    //    return a.id - b.id;
    //  })
      this.products = [...this.originProduct];
    },
  },
  mounted() {
    let interval = setInterval(()=>{
      this.showDiscount --;
      if (this.showDiscount == 0) {
        clearInterval(interval);
      }
    }, 1000);
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
.fade-enter-from {transform: translateY(-1000px);}
.fade-enter-active {transition: all 1s;}
.fade-enter-to {transform: translateY(0px);}

.fade-leave-from {opacity: 1;}
.fade-leave-active {transition: all 1s;}
.fade-leave-to {opacity: 0;}
</style>
