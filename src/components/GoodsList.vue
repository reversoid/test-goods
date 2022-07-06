<template>
    <div class="product-list-wrapper">
        <GoodItem v-for="product in products" :key="product.id" :product="product" :deleteCallback="deleteCallback"></GoodItem>
    </div>
</template>

<script>
import GoodItem from "./GoodItem.vue";

export default {
    name: "GoodList",
    components: {
        GoodItem,
    },
    props: {
        products: Array,
        deleteCallback: Function
    },
};
</script>
<style>
.product-list-wrapper {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}
</style>