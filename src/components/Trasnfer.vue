<template>
  <div class="transfer">
    <div class="transfer_box">
      <Profile :img=trasnfer.picture>
      </Profile>
      <div class="transfer_join">
        <p class="transfer_name"> <span>to:</span> <em> {{trasnfer.name}}</em></p>
        <span class="transfer_date">{{trasnfer.date}}</span>
      </div>
    </div>
    <div class="transfer_box">
      <span class="transfer_amount">{{ amoutCurreny(trasnfer.amount) }}</span>
    </div>
  </div>
</template>

<script>
import Profile from '@/components/Profile.vue'

export default {
  name: "Trasnfer",
  components: {
    Profile
  },
  props: {
    trasnfer :{
      type: Object,
      required: true
    }
  },
  methods:{
    amoutCurreny(amount) {
      return amount.toLocaleString('pt-br', { style:'currency' , currency:'BRL'} )
    }
  }
}
</script>

<style lang="scss">
  .transfer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: $c-white;
    box-shadow: 0px 4px 26px rgba(0, 0, 0, 0.06);
    border-radius: 6px;

    &_box {
      display: flex;
      align-items: center;
    }

    &_name {
      margin: 0;
      span {
        font-weight: 300;
        font-size: 1.2rem;
        line-height: 16px;
        color: #171D33;
        opacity: 0.4;
        margin-right: 4px;
      }

      em {
        font-weight: 500;
        font-style: normal;
        font-size: 1.4rem;
        line-height: 20px;
        letter-spacing: 0.2px;
        color: #171D33;
      }
    }

    &_date {
      font-size: 1.2rem;
      line-height: 18px;
    }

    &_amount {
      font-weight: 600;
      font-size: 1.6rem;
      line-height: 24px;
      text-align: right;
      letter-spacing: 0.1px;
      color: $c-pink-negative;
    }
  }
</style>
