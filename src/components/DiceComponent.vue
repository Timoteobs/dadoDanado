<template>
  <div class="body" >
    <div
      :class="{
        'frist-face': !start,
        'frist-rotation-face': start,
        intentionAttack: intention == 'attack',
        intentionDefend: intention == 'defend',
      }"
      v-if="number == '1'"
    >
      <div class="pip"></div>
    </div>

    <div
      :class="{
        'second-face': !start,
        'second-rotation-face': start,
        intentionAttack: intention == 'attack',
        intentionDefend: intention == 'defend',
      }"
      v-else-if="number == '2'"
    >
      <div class="pip"></div>
      <div class="pip"></div>
    </div>

    <div
      :class="{
        'third-face': !start,
        'third-rotation-face': start,
        intentionAttack: intention == 'attack',
        intentionDefend: intention == 'defend',
      }"
      v-else-if="number == '3'"
    >
      <div class="pip"></div>
      <div class="pip"></div>
      <div class="pip"></div>
    </div>

    <div
      :class="{
        'fourth-face': !start,
        'fourth-rotation-face': start,
        intentionAttack: intention == 'attack',
        intentionDefend: intention == 'defend',
      }"
      v-else-if="number == '4'"
    >
      <div class="colum">
        <div class="pip"></div>
        <div class="pip"></div>
      </div>
      <div class="colum">
        <div class="pip"></div>
        <div class="pip"></div>
      </div>
    </div>

    <div
      :class="{
        'fifth-face': !start,
        'fifth-rotation-face': start,
        intentionAttack: intention == 'attack',
        intentionDefend: intention == 'defend',
      }"
      v-else-if="number == '5'"
    >
      <div class="colum">
        <div class="pip"></div>
        <div class="pip"></div>
      </div>
      <div class="pip"></div>
      <div class="colum">
        <div class="pip"></div>
        <div class="pip"></div>
      </div>
    </div>

    <div
      :class="{
        'sixth-face': !start,
        'sixth-rotation-face': start,
        intentionAttack: intention == 'attack',
        intentionDefend: intention == 'defend',
      }"
      v-else
    >
      <div class="colum">
        <div class="pip"></div>
        <div class="pip"></div>
        <div class="pip"></div>
      </div>
      <div class="colum">
        <div class="pip"></div>
        <div class="pip"></div>
        <div class="pip"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataComponent",
  props: {
    number: String,
    intention: String,
    start: Boolean,
  },
};
</script>

<style scoped>
.body {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
  flex-wrap: wrap;
  align-content: center;
}

[class$="face"] {
  width: 100px;
  height: 100px;
  border-radius: 10%;
  margin: 15px;
}
.pip {
  background: black;
  width: 20px;
  height: 20px;
  border-radius: 50px;
  margin: 4px;
}

.frist-face {
  display: flex;
  justify-content: center;
  align-items: center;
}

.frist-rotation-face {
  display: flex;
  justify-content: center;
  align-items: center;
  animation: rotate 0.5s linear infinite;
}

.second-face {
  display: flex;
  justify-content: space-between;
}

.second-face .pip:nth-of-type(2) {
  align-self: flex-end;
}

.second-rotation-face {
  display: flex;
  justify-content: space-between;
  animation: rotate 0.5s linear infinite;
}

.second-rotation-face .pip:nth-of-type(2) {
  align-self: flex-end;
}

.third-face {
  display: flex;
  justify-content: space-between;
}

.third-face .pip:nth-of-type(2) {
  align-self: center;
}

.third-face .pip:nth-of-type(3) {
  align-self: flex-end;
}

.third-rotation-face {
  display: flex;
  justify-content: space-between;
  animation: rotate 0.5s linear infinite;
}

.third-rotation-face .pip:nth-of-type(2) {
  align-self: center;
}

.third-rotation-face .pip:nth-of-type(3) {
  align-self: flex-end;
}

.fourth-face {
  display: flex;
  justify-content: space-between;
}

.fourth-rotation-face {
  display: flex;
  justify-content: space-between;
  animation: rotate 0.5s linear infinite;
}

.colum {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.fifth-face {
  display: flex;
  justify-content: space-between;
}

.fifth-rotation-face {
  display: flex;
  justify-content: space-between;
  animation: rotate 0.5s linear infinite;
}

.fifth-face .pip:nth-of-type(2) {
  align-self: center;
}

.fifth-rotation-face .pip:nth-of-type(2) {
  align-self: center;
}

.sixth-face {
  display: flex;
  justify-content: space-between;
}

.sixth-rotation-face {
  display: flex;
  justify-content: space-between;
  animation: rotate 0.5s linear infinite;
}

.intentionAttack {
  background: red;
  width: 100px;
  height: 100px;
  border-radius: 10%;
  margin: 8px;
  padding: 6px;
}

.intentionDefend {
  background: yellow;
  width: 100px;
  height: 100px;
  border-radius: 10%;
  margin: 8px;
  padding: 6px;
}

@keyframes rotate {
  to {
    transform: rotate(360deg);
  }
}
</style>