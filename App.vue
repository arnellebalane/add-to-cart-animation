<template>
    <div class="app" id="app">
        <CartWidget ref="cart" />
        <AddToCartButton @click="$refs.cart.add()" />
    </div>
</template>

<script>
    import AddToCartButton from './components/AddToCartButton.vue';
    import CartWidget from './components/CartWidget.vue';

    export default {
        name: 'App',

        components: {
            AddToCartButton,
            CartWidget
        }
    };
</script>

<style scoped>
    .app {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .add-to-cart-button {
        margin-top: 50px;
    }
</style>
