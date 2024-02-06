
<template>
  <header>
    <h1 class="center">Widerstandsrechner</h1>
    <ResistorAdder @resistor-added="resistorAdded"/>
    <ResistorModifier :own_value="value" :own_nr="index" 
    v-for="(value, index) in resistors" :key="index" 
    @resistor-changed="resistorChanged"
    @remove-resistor="resistorRemoved"/>
    <CircuitDisplay :result="result" @ser-or-par-changed="connectionChanged"/>
  </header>
</template>

<script lang="ts">
import ResistorAdder from './components/ResistorAdder.vue';
import CircuitDisplay from './components/CircuitDisplay.vue';
import ResistorModifier from './components/ResistorModifier.vue';

export default {
    data() {
        return {
          result: 0,
          resistors: [],
          ser_or_par: false
        }
    },
    components: {
      ResistorAdder,
      CircuitDisplay,
      ResistorModifier
    },
    methods: {
        resistorAdded(res_value:any) {
          this.resistors.push(res_value);
          this.calculateResistance();
        },
        resistorRemoved(res_nr:any) {
          this.resistors.splice(res_nr, 1);
          console.log("Removed R" + res_nr)
          this.calculateResistance();
        },
        resistorChanged(new_res_value:any, res_nr:any) {
          this.resistors[res_nr] = new_res_value;
          this.calculateResistance();
        },
        calculateResistance() {
          console.log("calculating...")
          this.result = 0;
          if (this.ser_or_par){
            for (let i = 0; i < this.resistors.length; i++){
              this.result += this.resistors[i];
            }
          } else if (!this.ser_or_par) {
            if (this.resistors.length <= 0) {
              this.result = 0;
            } else {
              for (let i = 0; i < this.resistors.length; i++){
                this.result += 1 / this.resistors[i];
              }
              this.result = 1 / this.result;
            }
          }
          this.result = this.result.toFixed(3);
          console.log(this.result);
        },
        connectionChanged(new_ser_or_par:any){
          console.log("changed ser_to_pal");
          this.ser_or_par = new_ser_or_par;
          this.calculateResistance();
        }
    },
};
</script>


<style scoped>
@import "./styles/style.scss";
</style>
