<template>
  <table class="coin-price-table">
    <thead>
      <tr>
        <th colspan="2">자산</th>
        <th> 현재가 </th>
        <th> 변동률 </th>
        <th>거래금액(백만)</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="coin in coinData" :key="coin" class="row">
        <td>
          <img class="coin-img" :src="require(`@/assets/img/${coin.img_id}.png`)"/>
        </td>
        <td>
          <p>{{ coin.coin_knm }}</p>
          <p>({{coin.coin_code}}/KRW)</p>
        </td>
        <td :id="`${coin.coin_code}_price`"> price </td>
        <td :id="`${coin.coin_code}_fluc`"> 
          <p :id="`${coin.coin_code}_rate`"></p>
          <p :id="`${coin.coin_code}_fluctate`"></p>
           </td>
        <td :id="`${coin.coin_code}_trade`"> trade </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "Table",
  data() {
    return {
      coinCode: "",
      coinPrice: [],
    };
  },
  props: {
    coinData: Object,
  },
  beforeCreate() {
    this.axios
      .get("https://api.bithumb.com/public/ticker/ALL")
      .then((result) => {
        let data = result.data.data;
        console.log(data.BTC)
        this.coinCode = Object.keys(data);
        for (let i = 0; i < this.coinCode.length - 1; i++) {
            document.getElementById(`${this.coinCode[i]}_price`).innerText = this.comma(data[this.coinCode[i]].closing_price);
            document.getElementById(`${this.coinCode[i]}_rate`).innerText =  this.comma(data[this.coinCode[i]].fluctate_rate_24H);
            document.getElementById(`${this.coinCode[i]}_fluctate`).innerText =  "(" + this.comma(data[this.coinCode[i]].fluctate_24H) +")";
            document.getElementById(`${this.coinCode[i]}_trade`).innerText = this.comma((data[this.coinCode[i]].acc_trade_value_24H > 1000000 ? (data[this.coinCode[i]].acc_trade_value_24H / 1000000) : data[this.coinCode[i]].acc_trade_value_24H).toFixed(0)) + (data[this.coinCode[i]].acc_trade_value_24H > 1000000 ? "" : "");
          // this.coinPrice.push(data[this.coinCode[i]].closing_price);
        }

      });
  },
  methods: {
     comma(str) {
       if(str > 1){
         str = String(str);
       return str.replace(/(\d)(?=(?:\d{3})+(?!\d))/g, '$1,');
       } else {
         return str;
       }
    }
  },
};
</script>

<style>
@import "./../assets/Table.css";
</style>