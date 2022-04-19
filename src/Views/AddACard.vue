<template>
  <div id="AddACard">
    <h1>ADD NEW CARD</h1>
    <div class="activeCard">
      <p>NEW CARD</p>
      <Card class="CreateCard" :formData="formData" />
    </div>

    <form @submit.prevent="submit">
      <input
        type="text"
        placeholder="Card Number"
        v-model="formData.cardNumber"
        maxlength="20"
      />

      <input
        type="text"
        placeholder="Card Holders Name"
        v-model="formData.cardHolder"
      />

      <div class="expiry">
        <select
          name="expiryMonth"
          placeholder="expiryMonth"
          v-model="formData.expiryMonth"
          class="half"
        >
          <option value="" disabled selected hidden>Month</option>
          <option v-for="month in dateMonths" :key="month">{{ month }}</option>
        </select>

        <select
          name="expiryYear"
          placeholder="expiryYear"
          v-model="formData.expiryYear"
          class="half"
        >
          <option value="" disabled selected hidden>Year</option>
          <option v-for="year in dateYears" :key="year">{{ year }}</option>
        </select>
      </div>

      <select name="Vendor" v-model="formData.vendor">
        <option value="" disabled selected hidden>ninja</option>
        <option v-for="vendor in vendors" :key="vendor">{{ vendor }}</option>
      </select>
    </form>

    <button @click="switchAndEmitData">ADD CARD</button>
  </div>
</template>

<script>
import Card from "../Components/Card.vue";
export default {
  props: ["showWallet"],
  components: {
    Card,
  },
  data() {
    return {
      formData: {
        cardNumber: "",
        cardHolder: "",
        expiryMonth: "",
        expiryYear: "",
        vendor: "",
      },
      dateMonths: {
        1: "01",
        2: "02",
        3: "03",
        4: "04",
        5: "05",
        6: "06",
        7: "07",
        8: "08",
        9: "09",
        10: "10",
        11: "11",
        12: "12",
      },
      dateYears: {
        22: "22",
        23: "23",
        24: "24",
        25: "25",
        26: "26",
        27: "27",
      },
      vendors: {
        ninja: "Ninja",
        bitcoin: "Bitcoin Inc",
        blockchain: "Blockchain",
        evil: "Evil Corp",
      },
    };
  },
  methods: {
    switchAndEmitData() {
      this.$emit("newCardData", this.formData);
      this.$emit("switch");
    },
  },
};
</script>

<style>
#AddACard {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: "PT Mono", monospace;
  margin-top: 10%;
  height: 43%;
}

input {
  margin: 1rem;
  height: 3rem;
  border: 1px solid black;
  border-radius: 3px;
  width: 335px;
  font-family: "PT Mono", monospace;
  text-transform: uppercase;
}

select {
  margin: 1rem;
  height: 3rem;
  border: 1px solid black;
  border-radius: 3px;
  width: 340px;
}

.half {
  width: 155px;
}

.InputHoverText {
  height: 0px;
  width: 0px;
  font-size: 0.8rem;
  color: #999;
}

button {
  justify-self: flex-end;
  height: 4rem;
  width: 335px;
  border: 2px solid black;
  border-radius: 1rem;
  background-color: white;
  font-size: 1.5rem;
  font-family: "PT Mono", monospace;
  font-weight: bold;
}
</style>
