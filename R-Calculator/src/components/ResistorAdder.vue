
<template>
    <div>
        <label>Enter resistor value: </label>
        <input type="number" min="1" max="10000" 
        class="number-field-input" inputmode="numeric" 
        pattern="/d+" v-model="res_val">
        <button v-on:click="numberInput">Add</button>
    </div>
</template>

<style lang="scss">
    @import "../styles/style.scss";
</style>

<script lang="ts">

export default {
    data() {
        return {
            res_val: 0
        }
    },
    methods: {
        numberInput() {
            console.log("New resistor with value of: " + this.res_val);
            this.$emit('resistor-added', this.res_val);
        }
    },
    
};
</script>
