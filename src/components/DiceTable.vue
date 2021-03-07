<template>
  <div>
    <div class="alert">
      <v-alert
        v-model="alert"
        dismissible
        color="red"
        border="left"
        elevation="2"
        colored-border
      >
        Só são permitidos <strong>3 dados na mesa</strong>
      </v-alert>
    </div>
    <div class="diceTable">
      <h1>Dado danado</h1>

      <h3>Declare sua intenção</h3>

      <v-radio-group v-model="intention" mandatory>
        <v-radio label="Atacar" value="error"></v-radio>
        <v-radio label="Defender" value="primary"></v-radio>
      </v-radio-group>

      <v-btn @click="randonData" depressed :color="intention">
        Adicionar dado
      </v-btn>

      <div class="component">
        <div v-for="(data, index) in dataC" :key="index">
          <DataComponent :number="data.number" :start="toRollItem" />
        </div>
      </div>

      <div class="toRoll" v-if="dataC.length > 0">
        <v-btn
          @click="toRoll"
          depressed
          color="success"
          :loading="toRollItem"
          :disabled="toRollItem"
        >
          Rolar
        </v-btn>
        <v-btn
          @click="remove"
          depressed
          color="error"
          id="error"
          :disabled="toRollItem"
        >
          Remover
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
import DataComponent from "./DataComponent";
export default {
  name: "DiceTable",
  components: {
    DataComponent,
  },
  data: () => ({
    intention: String,
    dataC: [],
    toRollItem: false,
    alert: false,
  }),
  methods: {
    randonData: function () {
      if (this.dataC.length < 3) {
        this.dataC.push({
          id: Math.random(),
          number: Math.floor(Math.random() * 6 + 1).toString(),
        });
      } else {
        this.alert = true;
      }
    },
    remove: function () {
      this.dataC = [];
    },
    toRoll: function () {
      if (!this.toRollItem) {
        this.toRollItem = true;
        setTimeout(() => {
          for (let index = 0; index < this.dataC.length; index++) {
            this.dataC[index].number = Math.floor(
              Math.random() * 6 + 1
            ).toString();
          }
          this.toRollItem = false;
        }, 2000);
      }
    },
  },
};
</script>

<style>
.diceTable {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 50px;
}
.component {
  display: flex;
  align-items: center;
  justify-content: center;
}
.toRoll {
  display: flex;
  flex-direction: column;
  margin-top: 50px;
}
#error {
  margin-top: 10px;
}
.alert {
  display: flex;
  margin: 25px;
  justify-content: center;
}
</style>