
<template>
    <div>
        <label>R{{ own_nr }} value: </label>
        <input type="number" min="1" max="10000" 
        class="number-field-input" inputmode="numeric" 
        pattern="/d+" v-model="my_value" >
        <button v-on:click="changeValue">Change</button>
        <button v-on:click="removeResistor">Remove</button>
    </div>
</template>

<style lang="scss">
    @import "../styles/style.scss";
</style>

<script lang="ts">

export default {
    props: [
        'own_value', 'own_nr'
    ],
    data() {
        return {
            my_value: 0
        }
    },
    watch: {
        own_value: function(newValue, oldvalue) {
            this.my_value = oldvalue;
        }
    },
    // hier dann so mit onmount machen damit ich später dann auch value changen kann
    methods: {
        changeValue() {
            console.log("New value of resistor " + this.own_nr + " is: " + this.own_value);
            this.$emit('resistor-changed', this.own_value, this.own_nr)
        },
        removeResistor() {
            console.log("Removing R" + this.own_nr);
            this.$emit('remove-resistor', this.own_nr);
        }
    },
};
</script>
