<template>
  <div
    class="card"
    :class="[
      'cardColor',
      { bitcoin: this.cards.vendor == 'Bitcoin Inc' },
      { blockchain: this.cards.vendor == 'Blockchain' },
      { ninja: this.cards.vendor == 'Ninja' },
      { evil: this.cards.vendor == 'Evil Corp' },
    ]"
    @click="$emit('targetCard')"
  >
    <div class="cardHead">
      <div class="wifiChip">
        <img src="../assets/wifi_white.svg" alt="" class="Icon" />
        <img src="../assets/chip.svg" alt="Card chip" class="Icon Chip" />
      </div>
      <img :src="iconPath" alt="Vendor Icon" class="Vendor" />
    </div>

    <div class="textBlock">
      <p class="CardNumber white">
        {{ this.cards.cardNumber }}
      </p>
      <div class="Name">
        <p class="CardHolder white margintop-0">CARDHOLDER NAME</p>
        <p class="FirstnameLastname white margintop-10">
          {{ this.cards.cardHolder }}
        </p>
      </div>

      <div class="Validity">
        <p class="ExpirationDate white margintop-0">VALID THRU</p>
        <p class="MMYY white margintop-10">
          {{ this.cards.expiryMonth }}/{{ this.cards.expiryYear }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: { cards: Object},
   data() {
    return {
      currentIcon: 'ninja',
    };
  },
  methods: {
    pickIcon() {
       if (this.cards.vendor == 'Bitcoin Inc') {
         this.currentIcon = 'bitcoin';
       } else if (this.cards.vendor == 'Blockchain') {
         this.currentIcon = 'blockchain';
       } else if (this.cards.vendor == 'Ninja') {
         this.currentIcon = 'ninja';
       } else if (this.cards.vendor == 'Evil Corp') {
         this.currentIcon = 'evil';
       } else {
         console.log('poop')
       }
        return this.currentIcon;
     },
  },
   computed: {
    iconPath(){
      return require(`../assets/${this.currentIcon}.svg`)
    }
  },
  created() {
    this.pickIcon();
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&display=swap");
.card {
  width: 382px;
  height: 241px;
  border-radius: 5px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
  background-color: #222222;
  font-family: "PT Mono", monospace;
  border-radius: 10px;
}

.bitcoin {
  background-color: #ffae34;
}

.blockchain {
  background-color: #8b58f9;
}

.ninja {
  background-color: #222222;
}

.evil {
  background-color: #f33355;
}

.cardHead {
  display: flex;
  flex-wrap: wrap;
  width: 382px;
  justify-content: space-between;
}

.wifiChip {
  display: flex;
  flex-direction: column;
  padding: 1rem;
}

.white {
  color: white;
}

.Vendor {
  height: 50px;
  width: 50px;
  margin-top: 2%;
  margin-right: 2%;
}

.Icon {
  width: 50px;
  height: 50px;
}

.textBlock {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-left: 5%;
}

.CardNumber {
  width: 330px;
  font-style: normal;
  font-weight: normal;
  font-size: 25px;
  line-height: 0px;
  letter-spacing: 0.03em;
}

.Validity {
  margin-right: 5%;
  text-align: right;
}

.margintop-10 {
  margin-top: -10px;
}
.margintop-5 {
  margin-top: 5px;
}
.margintop-0 {
  margin-top: 0px;
}
</style>
