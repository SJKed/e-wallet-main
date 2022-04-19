<template>
  <div id="WalletView">
    <h1>E-WALLET</h1>
    <div class="activeCard">
      <p>ACTIVE CARD</p>
      <WalletActiveCard :activeCardInfo="activeCardInfo"/>
    </div>

    <div class="wallet">
      <WalletCard
        class="WalletCard"
        v-for="card in cards"
        :key="card.id"
        :cards="card"
        @targetCard="call(card)"
        
      />
    </div>
    <button class="AddButton" @click="$emit('switch')">ADD NEW CARD</button>
  </div>
</template>

<script>
import WalletCard from "../Components/WalletCard.vue";
import WalletActiveCard from "../Components/WalletActiveCard.vue";
export default {
  data() {
    return {
      activeCardInfo: {
        cardNumber: "7391 9261 8457 5372",
        cardHolder: "JURSTEDT SIMON",
        expiryMonth: "01",
        expiryYear: "26",
        vendor: "Bitcoin Inc",
      },
    };
  },
  props: ["showWallet", "cards"],
  components: {
    WalletCard,
    WalletActiveCard,
  },
  methods: {
    call(information) {
      console.log(information);
      this.activeCardInfo = information;
    },
  },
};
</script>

<style>
#WalletView {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
}

h1 {
  font-family: "Source Sans Pro", monospace;
  font-size: 30px;
  font-weight: bold;
  line-height: 1.5;
  letter-spacing: 0.03em;
  color: black;
}

.activeCard {
  text-align: center;
  margin-top: -5.2%;
}

.activeCard > p {
  font-size: 0.7rem;
  margin-bottom: 0;
}

.placeholderCard {
  width: 382px;
  height: 241px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
  background-color: #222222;
  font-family: "PT Mono", monospace;
  border-radius: 10px;
}

.wallet {
  display: grid;
  grid-template-rows: repeat(3, 15%);
  margin-top: 10%;
  height: 45%;
}

.AddButton {
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
