<template>
  <v-app>
    <v-main>
      <DiceTable/>
    </v-main>
  </v-app>
</template>

<script>
import DiceTable from './components/DiceTable';

export default {
  name: 'App',

  components: {
    DiceTable,
  },

  data: () => ({
    //
  }),
};
</script>
