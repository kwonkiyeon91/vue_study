<template>
  <div class="black-bg" v-if="modalPop == true">
    <div class="white-bg">
      <h4>{{ products[clickProduct].title }}</h4>
      <p>{{ products[clickProduct].content }}</p>
      <input v-model.number="month" /> 개월
      <!-- <input @input="month = $event.target.value" /> 개월 -->
      <p>{{month}} 개월 선택함</p>
      <p>{{ products[clickProduct].price * month}}</p>
      <button @click="closeModal">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'ModalYellow',
    data() {
        return {
            month: 1,
        }    
    },
    watch: {
        month(a){
            if ( a > 12) { 
                alert("12까지만 입력 가능합니다.");
                this.month = 1;
            } else if ( isNaN(a) ) {
                alert("숫자만 입력해주세요.");
                this.month = 1;
            } else if (a === 2) {
                alert("3개월부터 가능합니다.");
                this.month = 1;
            }
        }
    },
    props: {
        products: Array,
        clickProduct: Number,
        modalPop: Boolean
    },
    methods: {
        closeModal() {
           this.$emit('closeModal');
        }
    }
};
</script>

<style>
</style>