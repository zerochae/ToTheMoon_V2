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
          <img
            class="coin-img"
            :src="require(`@/assets/img/${coin.img_id}.png`)"
          />
        </td>
        <!-- <img v-else :src="require(`@/assets/img/${coin.img_id}1.png`)" /> -->
        <td>
          {{ coin.coin_code }}
        </td>
        <td :id="`${coin.coin_code}_pirce`">{{ coin.coin_code }}</td>
        <td :id="`${coin.coin_code}_rate`">{{ coin.coin_code }}</td>
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
      coin_price : "",
    };
  },
  props: {
    coinData: Object,
  },
  created() {
    this.axios
      .get("https://api.bithumb.com/public/ticker/ALL")
      .then((result) => {
        let data = result.data.data;
        console.log(data)
        this.coinCode = Object.keys(data);
        
        for(let i =0; i<this.coinCode.length; i++){
        this.coin_price.push(coin_price.coinCode[i])
        }

      });
  },
  methods: {},
};
</script>

<style>
</style>