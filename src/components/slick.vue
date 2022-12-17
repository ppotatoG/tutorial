<template>
    <div>
        <VueSlickCarousel v-bind="settings">
            <div><h1>1</h1></div>
            <div><h1>2</h1></div>
            <div><h1>3</h1></div>
            <div><h1>4</h1></div>
            <div><h1>5</h1></div>
            <div><h1>6</h1></div>
            <div><h1>7</h1></div>
            <div><h1>8</h1></div>
            <div><h1>9</h1></div>
            <div><h1>10</h1></div>
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
                "dots": true,
                "infinite": true,
                "slidesToShow": 3,
                "slidesToScroll": 1,
                "autoplay": true,
                "autoplaySpeed": 2000,
                "pauseOnDotsHover": true,
                "pauseOnFocus": true,
                "pauseOnHover": true
            }
        }
    }
}
</script>

<style lang="scss">
.slick-slide {
    background: gray;
}
</style>