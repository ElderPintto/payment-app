<template>
  <Hooper :itemsToShow="1.25" :centerMode="true">
    <Slide v-for="card in cards">
      <figure class="creditCard_img">
        <!-- <img :src="require(`../assets/${card.logo}`)" alt=""> -->
      </figure>
      <div class="creditCard_number">
        {{ card.number }}
      </div>
      <div class="creditCard_option">
        <div class="creditCard_name">
          {{ card.name }}
        </div>
        <div class="creditCard_date">
          {{ card.date }}
        </div>
      </div>
    </Slide>
  </Hooper>
</template>

<script>
import { Hooper, Slide } from 'hooper';
import 'hooper/dist/hooper.css';
export default {
  name: "Slide",
  // props: {
  //   cards :{
  //     type: Object,
  //     required: true
  //   }
  // },
  components: {
    Hooper,
    Slide,
  },
  data() {
    return {
      cards: [
        { logo: "visa-pay-logo.png", number:"1234567891234567",name: "Elder da Silva Pinto", date: "08/21"   },
        { logo: "visa-pay-logo.png", number:"1234567891234567",name: "Eliclicia", date: "08/21"   },
        { logo: "visa-pay-logo.png", number:"1234567891234567",name: "Edilson", date: "08/21"   }
      ]
    }
  },
}
</script>

<style lang="scss">

</style>
