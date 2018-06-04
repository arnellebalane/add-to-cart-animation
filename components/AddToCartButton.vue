<template>
    <button
        class="add-to-cart-button"
        v-bind="$attrs"
        v-on="$listeners"
    >
        Add to Cart
    </button>
</template>

<script>
    export default {
        name: 'AddToCartButton'
    };
</script>

<style scoped>
    .add-to-cart-button {
        display: inline-block;
        padding: 1.5em 3em;
        border: none;
        font: inherit;
        font-size: 18px;
        text-transform: uppercase;
        color: #fff;
        background-color: #ff3355;
        cursor: pointer;
        transition: opacity 300ms ease;
    }

    .add-to-cart-button:hover,
    .add-to-cart-button:focus {
        opacity: 0.5;
    }
</style>
