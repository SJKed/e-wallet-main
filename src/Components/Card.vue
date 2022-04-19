<template>
  <div class="card" :class="['cardColor',{none: formData.vendor == ''}, {bitcoin: formData.vendor == 'Bitcoin Inc'}, {blockchain: formData.vendor == 'Blockchain'}, {ninja: formData.vendor == 'Ninja'}, {evil: formData.vendor == 'Evil Corp'}]">
    <div class="cardHead">
      <div class="wifiChip">
        <img src="../assets/wifi_white.svg" alt="" class="Icon" />
        <img src="../assets/chip.svg" alt="Card chip" class="Icon Chip" />
      </div>
      <img :src="iconPath" alt="Vendor Icon" class="Vendor" :formData="formData.vendor"/>
    </div>

    <div class="textBlock">
      <p class="CardNumber white" :formData="formData.cardNumber">
        {{ formData.cardNumber }}
      </p>
      <div class="Name">
        <p class="CardHolder white margintop-0">CARDHOLDER NAME</p>
        <p class="FirstnameLastname white margintop-10">
          {{ formData.cardHolder }}
        </p>
      </div>

      <div class="Validity">
        <p class="ExpirationDate white margintop-0">VALID THRU</p>
        <p class="MMYY white margintop-10">
          {{ formData.expiryMonth }}/{{ formData.expiryYear }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: { formData: Object },
  data() {
    return {
      currentIcon: 'ninja',
    };
  },
  methods: {
    pickIcon() {
       if (this.formData.vendor == 'Bitcoin Inc') {
         this.currentIcon = 'bitcoin';
       } else if (this.formData.vendor == 'Blockchain') {
         this.currentIcon = 'blockchain';
       } else if (this.formData.vendor == 'Ninja') {
         this.currentIcon = 'ninja';
       } else if (this.formData.vendor == 'Evil Corp') {
         this.currentIcon = 'evil';
       } else {
         console.log('error')
       }
        return this.currentIcon;
     },
  },
   computed: {
    iconPath(){
      return require(`../assets/${this.currentIcon}.svg`)
    }
  },
  updated() {
    this.pickIcon();
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&display=swap");
.card {
  width: 382px;
  height: 241px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
  font-family: "PT Mono", monospace;
  border-radius: 10px;
}

.none {
  background-color: rgb(136, 136, 136);
}

.bitcoin {
  background-color: #FFAE34;
}

.blockchain {
  background-color: #8B58F9;
}

.ninja {
  background-color: #222222;
}

.evil {
  background-color: #F33355;
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
  text-align: left;
  font-size: 25px;
  line-height: 0px;
  letter-spacing: 0.03em;
}

.FirstnameLastname {
  text-align: left;
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
