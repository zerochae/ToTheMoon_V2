<template>
  <div>
    <Table :coinData="coinData"/>
  </div>
</template>

<script>
import coinData from "./assets/coinData";
import Table from "./components/Table.vue";

export default {
  name: "App",
  components: {
    Table,
  },
  data() {
    return {
      coinData: coinData,
    };
  },
};
</script>

<style>
@import "./assets/App.css";
</style>
