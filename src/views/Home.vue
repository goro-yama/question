<template>
  <div class="home">
    <input type="text" v-model="postcode">
    <button @click="callAPI()">住所自動入力</button>
    <p>Address：{{address}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      postcode: null,
      address: "",
    };
  },
  methods: {
    async callAPI() {
      const items = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.postcode}?fields=allAddress,?apikey=wqONvEtiLiOZVNU0yukUK2ktQop7OtAdEBcSK9p`);
      console.log(items);
      this.address = items.data[0].allAddress;
    }
  }
}
</script>
