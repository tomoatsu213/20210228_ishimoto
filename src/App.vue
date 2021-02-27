<template>
  <div>
    <input type="text" v-model="postcode" maxlength="7" />
    <button @click="input">住所自動入力</button>
    <p>Address :{{ address }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      postcode: "",
      address: "",
    };
  },

  methods: {
    input() {
      axios.get(
        `https://apis.postcode-jp.com/api/v4/postcodes/${this.postcode}?apiKey=NVnbH7DpQ1tKCTX1c9XhTH9uHehmCeWq4Z7sl6y`
      ).then((response) => {this.address= response.allAddress;});
    },
  },
};
</script>