<template>
    <div class="wrap">
        <VueSlickCarousel v-bind="settings">
            <div v-for="i in 10" v-bind:key="i"><p>{{ i }}</p></div>
        </VueSlickCarousel>
        <VueSlickCarousel v-bind="settings">
            <div v-for="i in 10" v-bind:key="i"><p>{{ i }}</p></div>
        </VueSlickCarousel>
    </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name: 'MyComponent',
    components: { VueSlickCarousel },
    data() {
        return {
            settings: {
                "arrows": false,
                "dots": true,
                "infinite": true,
                "slidesToShow": 3,
                "slidesToScroll": 1,
                "autoplay": true,
                "autoplaySpeed": 2000,
                "pauseOnDotsHover": true,
                "pauseOnFocus": true,
                "pauseOnHover": true,
                "adaptiveHeight": true
            }
        }
    }
}
</script>

<style lang="scss">
.slick {
    &-slider {
        & + .slick-slider {
            margin-top: 50px;
            .slick-slide > div {
                background: beige;
            }
        }
    }
    &-slide {
        > div {
            background: silver;
            margin: 5px;
        }
        p {
            text-align: center;
            font: {
                size: 50px;
                weight: bold;
            }
        }
    }
}
</style>