<template>
    <div class="all-wrapper">
        <div class="sorts">
            <div class="sorts__item">
                <button @click="sortProducts(true, 'price')" id="priceAsc" class="sorts-button">
                </button>
                <label for="priceAsc">По возрастанию цены</label>
            </div>
            <div class="sorts__item">
                <button @click="sortProducts(false, 'price')" id="priceDesc" class="sorts-button">
                </button>
                <label for="priceDesc">По убыванию цены</label>
            </div>
            <div class="sorts__item">
                <button @click="sortProducts(true, 'title')" id="titleAsc" class="sorts-button">
                </button>
                <label for="titleAsc">По возрастающему названию</label>
            </div>
            <div class="sorts__item">
                <button @click="sortProducts(false, 'title')" id="titleDesc" class="sorts-button">
                </button>
                <label for="titleDesc">По убывающему названию</label>
            </div>
        </div>
        <div class="product-list-wrapper">
            <GoodItem v-for="product in products" :key="product.id" :product="product" :deleteCallback="deleteCallback">
            </GoodItem>
        </div>
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
        deleteCallback: Function,
        sortProducts: Function
    },
};
</script>
<style lang="scss">
.sorts {
    display: flex;
    flex-wrap: wrap;
    .sorts__item:not(:last-child) {
        margin-bottom: 2px;
    }
    margin-bottom: 1rem;
    .sorts__item {
        display: flex;
        align-items: center;
        padding: 0.5rem;
    }
    .sorts-button {
        margin-right: 0.3rem;
        width: 1rem;
        height: 1rem;
        background-color:chocolate;
        border-radius: 50%;
        &:focus {
            box-shadow: 0 0 5px rgb(80, 80, 80);
        }
    }
}

.all-wrapper {
    display: flex;
    flex-direction: column;
}

.product-list-wrapper {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}
</style>