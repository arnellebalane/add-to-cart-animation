<template>
    <div class="cart-widget">
        <span
            ref="count"
            v-show="itemsCount"
            class="items-count"
        >
            {{ itemsCount }}
        </span>

        <img
            ref="icon"
            src="../images/cart.png"
            alt="Cart Icon" class="cart-icon"
        />
    </div>
</template>

<script>
    import anime from 'animejs';

    export default {
        name: 'CartWidget',

        data() {
            return {
                itemsCount: 0
            };
        },

        methods: {
            add() {
                this.itemsCount++;
                this.animate();
            },

            animate() {
                anime.timeline({
                    targets: this.$refs.icon,
                    duration: 90
                }).add({
                    scale: 0.8,
                    easing: 'easeInQuad'
                }).add({
                    scale: 1,
                    easing: 'easeOutQuad'
                });

                const count = anime.timeline({
                    targets: this.$refs.count,
                    duration: 90
                });

                if (this.itemsCount === 1) {
                    count.add({
                        scale: 0,
                        duration: 0
                    });
                }

                count.add({
                    scale: 1.2,
                    easing: 'easeInQuad'
                }).add({
                    scale: 1,
                    easing: 'easeOutQuad'
                });
            }
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
        font-size: 24px;
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
