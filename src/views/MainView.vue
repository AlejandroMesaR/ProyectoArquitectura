<template>
  <div class="main-view">
    <div class="processor">
      <div class="bus-component">
        <div class="bus">
          <Bus></Bus>
        </div>
        <div class=" control-unit">
          <ControlUnit />
        </div>
        <v-form class="form">
          <v-textarea v-model="data" class="text-field" label="Instrucciones" outlined no-resize></v-textarea>
         
          <div class="options">
            <v-btn style="background-color: #3E9855; color: white;" @click="transferData">Iniciar</v-btn>
          </div>
        </v-form>
      </div>
      <div class="component">
        <ALU />
      </div>
    </div>
    <div class="registro">
        <Records />
    </div>
    <div class=" memory-ram">
      <MemoryRam />
    </div>

  </div>
</template>

<script lang="ts">
import Vue from "vue";
import ControlUnit from "../components/ControlUnit.vue";
import ALU from "../components/ALU.vue";
import Bus from "../components/Bus.vue";
import MemoryRam from "@/components/MemoryRam.vue";
import Records from "../components/Records.vue";
import { mapMutations } from "vuex";

export default Vue.extend({
  name: "MainView",
  components: {
    ControlUnit,
    ALU,
    Bus,
    MemoryRam,
    Records,
  },
  data() {
    return {
      data: null,
      time: 5000,
    };
  },
  methods: {
    ...mapMutations("processor", ["transferDataMemoryToRecord"]),
    transferData() {
      this.transferDataMemoryToRecord({ data: this.data, time: this.time });
    },
  },
});
</script>

<style scoped>
.main-view {
  display: flex;
  flex-direction: row;
  align-items: center;
  background-image: url(../assets/fondo3.jpg);
  padding: 20px;
  border-radius: 4px;
}

.processor {
  display: flex;
  justify-content: center;
  margin-top: 20px;
  margin-right: 20px;
  
}

.component {
  margin-top: 95px;
  padding-left: 10px;
  border-radius: 4px;
  
  
}

.registro{
  border: 1px solid #ddd;
  padding: 10px;
  background-color: #626463;
  border-radius: 4px;
  color: white;
  
}

.control-unit {
  
  border: 1px solid #ddd;
  height: 140px;
  justify-content: center;
  align-items: center;
  background-color: #626463;
  color: white;
  
  border-radius: 4px;
}

.memory-ram {
  width: 400px;
  border: 1px solid #ddd;
  padding: 10px;
  background-color: #626463;
  border-radius: 4px;
  margin-left: 20px;
  color: white;
}

.text-field {
  padding: 10px;
  background-color: #fff;
  border-radius: 4px;
}

.form {
  border: 1px solid #ddd;
  padding: 30px;
  background-color: #fff;
  border-radius: 4px;
}

.bus-component {
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding-right: 10px;
}

.bus {
  border: 1px solid #ddd;
  height: 140px;
  justify-content: center;
  align-items: center;
  background-color: #626463;
  color: white;
  border-radius: 4px;
}

.options {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.options v-btn {
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
}

.options v-btn:hover {
  background-color: #0056b3;
}
</style>
