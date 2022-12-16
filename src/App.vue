<template>
    <div>
        <div v-for="product in products" :key="product">
            <img :src="product.image" />
            <h4 @click="모달창열렸니 = true">{{product.title}}</h4>
            <p>{{product.content}}</p>
            <p>{{product.price}}</p>
            <button @click="신고">허위매물신고</button><span> 신고수: {{num}}</span>
        </div>

        <div class="black-bg" v-if="모달창열렸니 == true">
            <div class="white-bg">
                <h4>상세페이지</h4>
                <p>상세페이지 내용</p>
                <button @click="모달창열렸니 = false">닫기</button>
            </div>
        </div>
    </div>
</template>

<script>
import oneRoom from './data.js';

export default {
  name: 'App',
  data() {
    return {
        모달창열렸니: false,
        // products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
        products: oneRoom,
        nums: 0
    }
  },
  methods: {
    신고() {
       return this.num ++
    }
  },
  components: {
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
    width: 100%;
    background: white;
    border-radius: 8px;
    padding: 20px;
}
</style>
