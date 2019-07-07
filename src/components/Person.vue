<template>
  <div class="person">
    <p>to: <strong>{{person.name}}</strong></p>
    <span>{{person.date}}</span>
    <span>$ {{person.amount}}</span>
  </div>
</template>

<script>
export default {
  name: "Person",
  props: {
    person :{
      type: Object,
      required: true
    }
  },
}
</script>

<style>

</style>
