<template>
  <div class="alu">
    <h2>ALU</h2>
    <div class="component">
      <v-row class="row">
        <v-col cols="6" class="label">Operando:</v-col>
        <v-col class="value">{{ operandCode }}</v-col>
      </v-row>
      <v-row class="row">
        <v-col cols="6" class="label">Ope 1:</v-col>
        <v-col class="value">{{ operandOne }}</v-col>
      </v-row>
      <v-row class="row">
        <v-col cols="6" class="label">Ope 2:</v-col>
        <v-col class="value">{{ operandTwo }}</v-col>
      </v-row>
      <v-row class="row">
        <v-col cols="6" class="label">Resultado:</v-col>
        <v-col class="value">{{ operandResult }}</v-col>
      </v-row>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { mapState } from "vuex";

export default Vue.extend({
  name: "ALU",
  computed: {
    ...mapState("processor", [
      "operandCode",
      "operandOne",
      "operandTwo",
      "operandResult",
    ]),
  },
});
</script>

<style scoped>
.alu {
  border-radius: 10px;
  padding: 10px;
  background-color: #626463;
  margin-bottom: 20px;
  border: 1px solid #ddd;
}

h2 {
  font-size: 20px;
  margin-bottom: 10px;
  color: white;
}

.component {
  border: 1px solid black;
  padding: 10px;
  margin-top: 10px;
  border-radius: 4px;
  background-color: #ffffff;
  width: 200px;
}

.v-row {
  margin-bottom: 10px;
}

.v-col {
  padding: 5px;
  font-weight: bold;
}

.v-col:last-child {
  font-weight: normal;
}

.row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
}

.label {
  font-weight: bold;
  width: 120px;
  color: #666;
}

.value {
  flex-grow: 1;
}

.value::after {
  content: "";
  display: block;
  height: 1px;
  background-color: #ddd;
}
</style>
