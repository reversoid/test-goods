<template>
    <div class="product" tabindex="0">
        <button @click="deleteCallback(this.product.id)" class="delete-btn"></button>
        <img class="product__img"
            :src="product.imgLink" alt="">
        <div class="product__info">
            <div>
                <h1 class="product__title">{{ product.title }}</h1>
                <p class="product__description">{{ product.description }}</p>
            </div>

            <p class="product__price">{{product.price}} руб.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "GoodItem",
    props: {
        product: {
            price: Number,
            title: String,
            description: String,
            imgLink: String,
        },
        deleteCallback: Function,
    }
};
</script>

<style lang="scss">
.product {
    position: relative;
    border-radius: 0.25rem;
    width: 20.75rem;
    height: 26.4375rem;
    background-color: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    color: #3F3F3F;
    cursor: pointer;


    .delete-btn {
        pointer-events: none;
        opacity: 0;
        position: absolute;
        top: -0.75rem;
        right: -0.75rem;
        background-color: #FF8484;
        border-radius: 0.625rem;
        width: 2rem;
        height: 2rem;
        transition: 0.15s linear;
        background-image: url('../assets/delete.svg');
        background-size: 50%;
        background-repeat: no-repeat;
        background-position: center;
    }


    .product__info {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: calc(100% - 13.5rem + 1rem);
        padding: 1rem;
        padding-bottom: 1.5rem;
    }

    .product__img {
        width: 100%;
        height: 12.5rem;
        object-fit: cover;
        border-top-right-radius: inherit;
        border-top-left-radius: inherit;
    }

    .product__title {
        margin-bottom: 1rem;
        font-size: 1.25rem;
        font-weight: 600;
    }

    .product__description {
        font-size: 1rem;
        height: 5rem;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: wrap;
        margin-bottom: 2rem;
    }

    .product__price {
        font-weight: 600;
        font-size: 1.5rem;
    }
}

.product:hover .delete-btn {
    opacity: 1;
    pointer-events: initial;
}

.product:focus .delete-btn {
    opacity: 1;
    pointer-events: initial;
}
</style>
