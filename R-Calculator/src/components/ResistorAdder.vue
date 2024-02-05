
<template>
    <div>
        <label>Enter resistor value: </label>
        <input type="number" min="1" max="10000" 
        class="number-field-input" inputmode="numeric" 
        pattern="/d+" v-model="numberInput">
    </div>
</template>

<style lang="scss">
    @import "./styles/_variables.scss";
</style>

<script lang="ts">

export default ({
    data() {
        return {
            res_val: 0
        }
    },
    methods: {
        numberInput() {
            console.log("New resistor with value of: " + this.res_val);
        }
    },
})
</script>
