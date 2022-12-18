<template>
    <div class="wrap">
        <div class="multiple_slides">
            <VueSlickCarousel v-bind="multipleSlides" ref="multipleSlides" @afterChange="multipleSlideChange">
                <div v-for="i in 10" v-bind:key="i"><p>{{ i }}</p></div>
            </VueSlickCarousel>
            <div class="button_wrap">
                <button @click="slidePrev" v-if="multipleCurIndex === 0" disabled>이전</button>
                <button @click="slidePrev" v-else>이전</button>

                <button @click="slideNext" v-if="multipleCurIndex === multipleSlideLength" disabled>다음</button>
                <button @click="slideNext" v-else>다음</button>
            </div>
        </div>

        <div class="single_slides">
            <VueSlickCarousel v-bind="singleSlides" ref="singleSlides" @afterChange="singleSlideChange">
                <div v-for="i in 10" v-bind:key="i"><p>{{ i }}</p></div>
            </VueSlickCarousel>
            <div class="button_wrap">
                <p>{{ `${chgNbrDigits(singleSlideCurIdx + 1)} / ${chgNbrDigits(singleSlideLength + 1)}` }}</p>
                <button v-if="!isSlidePlay" @click="autoPlayToggle">재생</button>
                <button v-else @click="autoPlayToggle">멈춤</button>
            </div>
        </div>
    </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name: 'MyComponent',
    components: { VueSlickCarousel },
    methods: {
        slidePrev: function() {
            this.$refs.multipleSlides.prev();
        },
        slideNext: function() {
            this.$refs.multipleSlides.next();
        },
        multipleSlideChange(e){
            this.multipleCurIndex = e;
        },
        singleSlideChange(e){
            this.singleSlideCurIdx = e;
        },
        autoPlayToggle() {
            this.isSlidePlay = !this.isSlidePlay;
            this.isSlidePlay ? this.$refs.singleSlides.play() : this.$refs.singleSlides.pause();
        },
        chgNbrDigits(number) {
            return number.toString().padStart(2, '0');
        }
    },
    data() {
        return {
            isSlidePlay: true,
            multipleCurIndex: 0,
            multipleSlideLength: 9 - 3,
            multipleSlides: {
                "arrows": false,
                "dots": true,
                "slidesToShow": 4,
                "slidesToScroll": 1,
                "autoplay": false,
                "autoplaySpeed": 2000,
                "adaptiveHeight": true,
                "draggable": false
            },
            singleSlideLength: 9,
            singleSlideCurIdx: 0,
            singleSlides: {
                "infinite": true,
                "autoplay": true,
                "autoplaySpeed": 1000,
                "adaptiveHeight": true,
                "pauseOnFocus": true,
                "pauseOnHover": true
            }
        }
    }
}
</script>

<style lang="scss">
.wrap {
    overflow: hidden;
}
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
.button_wrap {
    position: absolute;
    bottom: 30px;
    right: 0;
    width: max-content;
    display: flex;
    margin: 0;
    padding: 0;
    gap: 10px;
    button {
        display: block;
    }
}
.multiple_slides {
    position: relative;
    padding-bottom: 50px;
    .slick {
        &-slide > div {
            background: beige;
        }
        &-dots {
            position: initial;
            display: flex !important;
            align-items: flex-end;
            width: 80%;
            li {
                display: block;
                width: 100%;
                margin: 0;
                height: max-content;
                button {
                    display: block;
                    width: 100%;
                    background: silver;
                    height: 4px;
                    padding: 0;
                    opacity: .4;
                    transition: width .2s;
                    &::before {
                        display: none;
                    }
                }
                &:nth-last-child(-n + 3) {
                    display: none;
                }
                &.slick-active {
                    width: 150%;
                    button{
                        opacity: 1;
                    }
                }
            }
        }
    }
}
.single_slides {
    position: relative;
    .button_wrap {
        right: 40px;
    }
}
</style>