<template>
    <GoodItem v-for="product in products" :key="product.id" :product="product" :deleteCallback="deleteCallback"></GoodItem>
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
