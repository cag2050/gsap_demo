<template>
    <div class="hello">
        <input v-model.number="number" type="number" step="20">
        <p ref="changedContainer">{{ animatedNumber }}</p>
    </div>
</template>

<script>
import {TweenLite} from 'gsap'
// let TweenLite = require('gsap/src/minified/TweenLite.min.js')

export default {
    name: '',
    data () {
        return {
            number: 0,
            tweenedNumber: 0
        }
    },
    created () {

    },
    mounted () {
        console.log(TweenLite)
    },
    computed: {
        animatedNumber () {
            // return this.number.toFixed(0)
            return this.tweenedNumber.toFixed(0)
        }
    },
    watch: {
        number: newValue => {
            TweenLite.to(this.refs.changedContainer, 0.5, { tweenedNumber: newValue })
        }
    }
}
</script>

<style>

</style>
