<template>
    <div class="hello">
        <p>input框，数字步长为10</p>
        <input v-model.number="number" type="number" step="10">
        <p id="changeContainer">{{ animatedNumber }}</p>
        <button @click="addNum">点击加10</button>
        <button @click="minusNum">点击减10</button>
    </div>
</template>

<script>
// import {TweenMax, Circ} from 'gsap'
import {TweenLite, Circ} from 'gsap'

export default {
    name: '',
    data () {
        return {
            number: 10000,
            tweenedNumber: 10000
        }
    },
    created () {
        // console.log(TweenLite)
    },
    mounted () {

    },
    methods: {
        addNum () {
            this.number += 10
        },
        minusNum () {
            this.number -= 10
        }
    },
    computed: {
        animatedNumber () {
            return this.tweenedNumber.toFixed(0)
        }
    },
    watch: {
        number (newValue) {
            let _this = this
            TweenLite.to(this.$data, 0.5, {
                tweenedNumber: newValue,
                onUpdate () {
                    document.getElementById('changeContainer').innerHTML = parseInt(_this.tweenedNumber.toFixed(0)).toLocaleString()
                },
                ease: Circ.easeOut
            })
        }
    }
}
</script>

<style>

</style>
