<template>
  <table class="coin-price-container">
    <thead>
      <tr>
        <th colspan="2">Coin</th>
        <th>Price</th>
        <th>Rate</th>
        <th>Amount</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="coin in coinData" :key="coin">
        <td>
          <img class="coin-img" :src="require(`@/assets/img/${coin.img_id}.png`)"/>
        </td>
        <td>
          {{ coin.coin_code }}
        </td>
        <td :id="`${coin.coin_code}_price`">{{ coin.coin_code }}</td>
        <td :id="`${coin.coin_code}_rate`">{{}}</td>
        <td :id="`${coin.coin_code}_amount`">{{ coin.coin_code }}</td>
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
        this.coinCode = Object.keys(data);
        for (let i = 0; i < this.coinCode.length - 1; i++) {
          console.log(this.coinCode[i]);
          if (
            document.getElementById(`${this.coinCode[i]}_price`).innerText !=
            null
          )
            document.getElementById(`${this.coinCode[i]}_price`).innerText =
              data[this.coinCode[i]].closing_price;
          this.coinPrice.push(data[this.coinCode[i]].closing_price);
        }

        console.log(this.coinPrice);
      });
  },
  methods: {},
};
</script>

<style>
</style>