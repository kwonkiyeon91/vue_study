<template>
  <div>
    <div class="discount">
      <h4>지금 결제하면 {{showDiscount}}%할인</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DiscountBanner',
  props: {
    showDiscount: Number
  }
};
</script>

<style>
</style>