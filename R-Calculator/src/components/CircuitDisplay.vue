<template>
    <div>
        <img id="parallel-img"/>
        <img id="serial-img"/>
        <button id="parallel-btn"></button>
        <button id="serial-btn"></button>
        <label>The total value of the resistors is {{  }}</label>
    </div>
</template>

<style lang="scss">

    @import "../styles/style.scss";
</style>

<script lang="ts">
export default ({
    props: [
        'result'
    ],
    data() {
        return {
            left_or_right: true, // false is right and true is left
        }
    },
})
</script>

<!--
Here are two images corresponding to the two circuit types.
The button should be exactly in the middle of both and depending on which
side is clicked the other one will get more grey and the other one will appear.
Also the new result should be displayed below somewhere
-->