<template>
    <div class="app" id="app">
        <CartWidget />
    </div>
</template>

<script>
    import CartWidget from './components/CartWidget.vue';

    export default {
        name: 'App',

        components: {
            CartWidget
        }
    };
</script>
