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
      <div>
        <img
          src="../assets/diceA.png"
          @click="randonData('attack')"
          class="dice"
          id="diceA"
        />
        <img
          src="../assets/diceD.png"
          @click="randonData('defend')"
          class="dice"
          id="diceD"
        />
      </div>

      <div class="component">
        <div v-for="(data, index) in dataC" :key="index">
          <DiceComponent
            :number="data.number"
            :start="toRollItem"
            :intention="data.intention"
            v-if="data.intention == 'defend'"
          />
          <DiceComponentAttack
            :number="data.number"
            :start="toRollItem"
            :intention="data.intention"
            v-else
          />
        </div>
      </div>

      <div class="toRoll" v-if="dataC.length > 0">
        <v-btn
          @click="toRoll"
          depressed
          color="primary"
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
import DiceComponent from "./DiceComponent";
import DiceComponentAttack from "./DiceComponentAttack";
export default {
  name: "DiceTable",
  components: {
    DiceComponent,
    DiceComponentAttack,
  },
  data: () => ({
    intentionState: String,
    dataC: [],
    toRollItem: false,
    alert: false,
  }),
  methods: {
    randonData: function (intention) {
      if (intention !== this.intentionState) {
        this.dataC = [];
      }
      if (this.dataC.length < 3) {
        this.dataC.push({
          id: Math.random(),
          number: Math.round(Math.random() * 5 + 1).toString(),
          intention,
        });
        this.intentionState = intention;
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
            this.dataC[index].number = Math.round(
              Math.random() * 5 + 1
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

.dice {
  width: 130px;
  height: 130px;
}

#diceA {
  margin-right: 5px;
}
#diceD {
  margin-left: 5px;
}

.testmove {
  display: block;
  position: absolute;
  top: 0;
  height: 150px;
  width: 150px;
  margin: 200px;
  background: #333;
  color: white;
}
</style>