<template>
  <div id="app">
    <Wallet v-if="showWallet" @switch="showWallet = false" :cards="cards" />
    <AddACard
      v-if="!showWallet"
      @switch="showWallet = true"
      @newCardData="logNewCard"
    />
  </div>
</template>

<script>
import AddACard from "./Views/AddACard.vue";
import Wallet from "./Views/Wallet.vue";
export default {
  components: {
    AddACard,
    Wallet,
  },
  data() {
    return {
      showWallet: true,
      cards: [
        {
          id: 0,
          cardNumber: "7391 9261 8457 5372",
          cardHolder: "JOHNSSON STEFAN",
          expiryMonth: "01",
          expiryYear: "26",
          vendor: "Bitcoin Inc",
        },
        {
          id: 1,
          cardNumber: "7432 4324 4325 5324",
          cardHolder: "DRAKAKI EROFILI",
          expiryMonth: "05",
          expiryYear: "22",
          vendor: "Blockchain",
        },
      ],
    };
  },
  methods: {
    logNewCard(value) {
      //push the new card to the cards array and give it an id
      this.cards.push({
        id: this.cards.length,
        cardNumber: value.cardNumber,
        cardHolder: value.cardHolder,
        expiryMonth: value.expiryMonth,
        expiryYear: value.expiryYear,
        vendor: value.vendor,
      });
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro:wght@200&display=swap");
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&display=swap");

#app {
  margin-left: auto;
  margin-right: auto;
  width: 420px;
  height: 890px;
  border-radius: 3rem;
  border: 2px solid black;
  text-transform: uppercase;
}
</style>
