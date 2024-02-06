<template>
    <div>
        <!--
            <img id="parallel-img" class="image" src="../images/parallel.png"/>
            <img id="serial-img" class="image" src="../images/serial.png"/>
            
        -->
        <p></p>
        <div class="two-btn center">
            <button class="L-btn" v-on:click="changeToSer">Parallel</button>
            <button class="R-btn" v-on:click="changeToPar">Seriell</button>
        </div>
        <p></p>
        <label class="center">Der Gesammtwiderstand beträgt {{ result }} <span>&#8486;</span></label>
    </div>
</template>

<style lang="scss">

    @import "../styles/style.scss";
</style>

<script lang="ts">
export default {
    props: [
        'result'
    ],
    data() {
        return {
            ser_or_par: true, // false is ser and true is par
        }
    },
    methods: {
        changeToSer() {
            this.ser_or_par = false;
            this.$emit('ser-or-par-changed', this.ser_or_par)
        },
        changeToPar() {
            this.ser_or_par = true;
            this.$emit('ser-or-par-changed', this.ser_or_par)
        }
    }
};
</script>

<!--
Here are two images corresponding to the two circuit types.
The button should be exactly in the middle of both and depending on which
side is clicked the other one will get more grey and the other one will appear.
Also the new result should be displayed below somewhere
-->
