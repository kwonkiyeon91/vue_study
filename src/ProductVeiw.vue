<template>
  <div class="product-card">
    <img :src="product.image" />
    <h4 @click="openModal">
      {{ product.title }}
    </h4>
    <p>{{ product.content }}</p>
    <p>{{ product.price }}</p>
    <!-- <button @click="increase;">허위매물신고</button><span> 신고수: {{ num }}</span> -->
  </div>
</template>

<script>
export default {
    name: 'ProductVeiw',
    props: {
        product: Object,
    },
    methods: {
        openModal() {
            this.$emit('openModal', this.product.id)
        }
    }
};
</script>

<style>
</style>