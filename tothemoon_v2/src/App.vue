<template>
  <div class="container">
    <Nav/>
    <News/>
    <div class="section">
      <div class="side-bar">
        <div class="search-bar-box">
          <input class="search-input" type="text" />
          <input type="submit" class="search-submit" value="🛠️" />
        </div>
        <div class="table-box">
          <Table :coinData="coinData" />
        </div>
      </div>
      <div class="content">
      </div>
    </div>
    <Footer/>
  </div>
</template>

<script>
import coinData from "./assets/coinData";
import Table from "./components/Table.vue";
import Nav from "./components/Nav.vue";
import Footer from "./components/Footer.vue";
import News from "./components/News.vue";

export default {
  name: "App",
  components: {
    Table,
    Footer,
    Nav,
    News,
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
