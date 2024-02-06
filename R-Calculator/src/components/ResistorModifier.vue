
<template>
    <div class="container">
        <label class="R">R{{ own_nr }}: 
            <input type="number" min="1" max="10000" 
            class="number-field-input" inputmode="numeric" 
            pattern="/d+" v-model="my_value" >
        </label>
        <div class="two-btn center">
            <button class="L-btn" v-on:click="changeValue">
                <img class="btn-image" src="../images/confirm.png">
            </button>
            <button class="R-btn" v-on:click="removeResistor">
                <img class="btn-image" src="../images/remove.png">
            </button>
        </div>
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
        own_value: function(newValue) {
            this.my_value = newValue;
        }
    },
    mounted() {
        this.my_value = this.own_value;
    },
    // hier dann so mit onmount machen damit ich später dann auch value changen kann
    methods: {
        changeValue() {
            console.log("New value of resistor " + this.own_nr + " is: " + this.own_value);
            this.$emit('resistor-changed', this.my_value, this.own_nr)
        },
        removeResistor() {
            this.$emit('remove-resistor', this.own_nr);
        }
    },
};
</script>
