<template>
    <div class="hello">
        <input v-model.number="number" type="number" step="20">
        <p>{{ animatedNumber }}</p>
    </div>
</template>

<script>
import {TweenLite} from 'gsap'

export default {
    name: '',
    data () {
        return {
            number: 0,
            tweenedNumber: 0
        }
    },
    computed: {
        animatedNumber () {
            // return this.number.toFixed(0)
            return this.tweenedNumber.toFixed(0)
        }
    },
    watch: {
        number: newValue => {
            TweenLite.to(this.data, 0.5, { tweenedNumber: newValue })
        }
    }
}
</script>

<style>

</style>
