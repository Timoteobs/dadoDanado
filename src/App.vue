<template>
  <v-app id="table">
    <v-main>
      <DiceTable />
    </v-main>
  </v-app>
</template>

<script>
import DiceTable from "./components/DiceTable";

export default {
  name: "App",

  components: {
    DiceTable,
  },

  data: () => ({
    //
  }),
};
</script>

<style>
  #table{
    background-image: url('./assets/bg.webp');
    background-size: cover;
  }
  h1, h2, h3 {
    color: #fff;
  }
</style>