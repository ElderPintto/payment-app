<template>

  <main>
    <h1 class="warningMode">view in mobile mode</h1>
    <Header></Header>
    <Hooper :itemsToShow="1.25" :centerMode="true" class="creditCard">
      <Slide v-for="card in cards" class="creditCard_item" :style="{background: card.color}" :key="card.number">
        <figure class="creditCard_img">
          <img :src="require(`../assets/${card.logo}`)" alt="">
        </figure>
        <div class="creditCard_number">

          {{  criptCard(card.number ) }}
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
    <SelectionOperation :operations="operations" @cliqueaqui="selectTransfer()"></SelectionOperation>
    <Search v-model="searchT"></Search>
      <Transfers

        :transfers="filterList">
      </Transfers>
      <!-- <h3 class="noResult">
        No results of  <span>"{{ searchT }}"</span>
      </h3> -->
    <Menu></Menu>
  </main>
</template>

<script>
import Header from "@/components/Header.vue";
import { Hooper, Slide } from 'hooper';
import 'hooper/dist/hooper.css';

import Search from "@/components/Search.vue";
import Transfers from "@/components/Transfers.vue";
import SelectionOperation from "@/components/SelectionOperation.vue";
import Menu from "@/components/Menu.vue";


export default {
  name: "home",
  components: {
    Header,
    Hooper,
    Slide,
    SelectionOperation,
    Search,
    Transfers,
    Menu
  },
  data() {
    return {
      searchT: "",
      transfersView: "send",
      transfers:[
          {id:"12345", type: "send", picture:"rebeca.jpg", name:"rebeca Oliveira", date: "2019-07-27T17:17:00Z", amount: 972},
          {id:"54321", type: "send", picture:"rebeca.jpg", name:"rebeca Giovanni", date: "2019-07-26T17:17:00Z", amount: 150},
          {id:"51423", type: "send", picture:"rebeca.jpg", name:"rebeca Aguiar", date: "2019-07-25T17:17:00Z", amount: 972},
          {id:"32514", type: "send", picture:"rebeca.jpg", name:"rebeca Reis", date: "2019-07-24T17:17:00Z", amount: 972},
          {id:"34512", type: "send", picture:"rebeca.jpg", name:"rebeca Teste", date: "2019-07-23T17:17:00Z", amount: 972},
          {id:"15243", type: "received", picture:"rebeca.jpg", name:"Joao Nascimento", date: "2019-07-22T17:17:00Z", amount: 1000},
          {id:"42315", type: "received", picture:"rebeca.jpg", name:"received Franz Ferdinand", date: "2019-07-21T17:17:00Z", amount: 170},
          {id:"35142", type: "received", picture:"rebeca.jpg", name:"received John Doe", date: "2019-07-20T17:17:00Z", amount: 72},
        ],
      cards: [
        { logo: "visa-pay-logo.png", number:"1234567891234567",name: "Elder Pinto", date: "08/21", color:"linear-gradient(100deg, rgba(34,193,195,1) 0%, rgba(45,253,198,1) 100%)"   },
        { logo: "visa-pay-logo.png", number:"1234567891234567",name: "rebeca Oliveira", date: "08/21", color:"linear-gradient(100deg, rgba(17,105,106,1) 0%, rgba(156,45,253,1) 100%)"   },
        { logo: "visa-pay-logo.png", number:"1234567891234567",name: "rebeca", date: "08/21", color:"black"   }
      ],
      operations: [
        {id:"1", name: "send", active: true},
        {id:"2", name: "received", active: false},
      ]
    }
  },
  computed: {
    filterList() {
      return this.transfers.filter( item => {

        if (item.type == this.transfersView) {
          return item.name.toLowerCase().includes(this.searchT.toLowerCase());
        }else if(!item)  {
          return [{name:"Nenhum item"}]

        }
      })
    }
  },
  methods: {
    criptCard(cardNumber) {
      let numberArr = [...cardNumber].slice(-4).join("");
      return "**** **** **** " + numberArr
    },
    selectTransfer() {
      this.transfersView = event.target.innerText;

      this.operations.map( item => {

        if (item.name == event.target.innerText) {
          item.active = true
        }else {
          item.active = false
        }

      });
    },
  }
};
</script>
<style lang="scss">

.noResult,
.warningMode {
  font-size: 20px;
  text-align: center;

  span {
    color: $c-pink-negative
  }
}

.warningMode {
  color: $c-orange-negative
}

.creditCard {
  margin: 14px 14px 0 14px;

  &_item {
    color: #fff;
    display: flex;
    flex-direction:  column;
    justify-content: space-between;
    padding: 15px 25px 20px;
    opacity: 0.5;
    transform: scale(0.9);
    border-radius: 6px;
    transition: all 800ms;
    max-height: 174px;

    &.is-active {
      opacity: 1;
      transform: scale(1);
      box-shadow: 0px 8px 28px rgba(#424242, 0.6);
    }
  }

  &_img {

  }
  &_number {
    font-weight: normal;
    font-size: 20px;
    line-height: 26px;
    letter-spacing: 3px;
  }
  &_option {
    display: flex;
    justify-content: space-between;
  }
  &_name {
      font-weight: 500;
      font-size: 16px;
      line-height: 24px;
      letter-spacing: 0.1px;

    &::before {
      display: block;
      content: "Card holder";
      font-style: normal;
      font-weight: 300;
      font-size: 12px;
      line-height: 20px;
      opacity: 0.8;

      letter-spacing: 0.4px;
      text-transform: uppercase;
    }
  }
  &_date {
    font-weight: 500;
    font-size: 16px;
    line-height: 24px;
    text-align: right;
    letter-spacing: 0.1px;

    &:before {
      content: "Expires";
      display: block;
      font-style: normal;
      font-weight: 300;
      font-size: 12px;
      line-height: 20px;
      opacity: 0.8;
      text-transform: uppercase;
    }
  }

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

}
</style>


