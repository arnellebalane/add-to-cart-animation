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

        <svg>
            <path ref="larc" d="M 41.5 146.683956 A 77 77 0 1 1 118.5 13.3160439" stroke-dasharray="0 483.805269" />
            <path ref="rarc" d="M 41.5 146.683956 A 77 77 0 1 0 118.5 13.3160439" stroke-dasharray="0 483.805269" />
        </svg>
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

        mounted() {
            anime({
                targets: this.$el,
                duration: 700,
                scale: [1.2, 1],
                opacity: [0, 1],
                easing: 'easeOutQuad'
            });
        },

        methods: {
            add() {
                setTimeout(() => this.itemsCount++, 275);
                this.animate();
            },

            animate() {
                anime({
                    duration: 400,
                    easing: 'easeInExpo',
                    update: animation => {
                        const dashArray = (483.805269 / 2) * (animation.progress / 100);
                        this.$refs.larc.setAttribute('stroke-dasharray', `${dashArray} 483.805269`);
                        this.$refs.rarc.setAttribute('stroke-dasharray', `${dashArray} 483.805269`);

                        const dashOffset = -(483.805269 / 2) * (animation.progress / 100);
                        this.$refs.larc.setAttribute('stroke-dashoffset', dashOffset);
                        this.$refs.rarc.setAttribute('stroke-dashoffset', dashOffset);
                    }
                });

                anime.timeline({
                    targets: this.$refs.icon,
                    duration: 90
                }).add({
                    scale: 0.8,
                    delay: 275,
                    easing: 'easeInQuad'
                }).add({
                    scale: 1,
                    easing: 'easeOutQuad'
                });

                const count = anime.timeline({
                    targets: this.$refs.count,
                    duration: 90
                });

                if (!this.itemsCount) {
                    count.add({
                        scale: 0,
                        duration: 0
                    });
                }

                count.add({
                    scale: 1.2,
                    delay: 275,
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
        width: 160px;
        height: 160px;
        border: 6px solid #3a3a3a;
        border-radius: 50%;
        position: relative;
    }

    .items-count {
        width: 60px;
        height: 60px;
        border: 5px solid #fff;
        border-radius: 50%;
        position: absolute;
        top: calc(50% - 30px - 69.2820323px);
        left: calc(50% - 30px + 40px);
        z-index: 1;
        font-size: 23px;
        line-height: 50px;
        text-align: center;
        color: #fff;
        background-color: #ff3355;
    }

    .cart-icon {
        width: 65px;
        height: 65px;
    }

    svg {
        width: 160px;
        height: 160px;
        position: absolute;
        top: -6px;
        left: -6px;
    }

    path {
        stroke: #ff3355;
        stroke-width: 6;
        fill: none;
    }
</style>
