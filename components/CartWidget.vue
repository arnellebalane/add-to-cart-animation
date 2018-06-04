<template>
    <div class="cart-widget">
        <span v-if="itemsCount" class="items-count">{{ itemsCount }}</span>
        <img src="../images/cart.png" alt="Cart Icon" class="cart-icon">
    </div>
</template>

<script>
    export default {
        name: 'CartWidget',

        data() {
            return {
                itemsCount: 0
            };
        }
    };
</script>

<style scoped>
    .cart-widget {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 150px;
        height: 150px;
        border: 6px solid #3a3a3a;
        border-radius: 50%;
        position: relative;
    }

    .items-count {
        width: 50px;
        height: 50px;
        border: 5px solid #fff;
        border-radius: 50%;
        position: absolute;
        top: 0;
        right: 0;
        font-size: 26px;
        line-height: 50px;
        text-align: center;
        color: #fff;
        background-color: #ff3355;
    }

    .cart-icon {
        width: 65px;
        height: 65px;
    }
</style>
