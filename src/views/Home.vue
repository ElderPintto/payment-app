<template>
  <main>
    <Header></Header>
    <Search></Search>
    <Transfers
      :transfers="transfers">
    </Transfers>
  </main>
</template>

<script>
import Header from "@/components/Header.vue";
import Search from "@/components/Search.vue";
import Transfers from "@/components/Transfers.vue";

export default {
  name: "home",
  components: {
    Header,
    Search,
    Transfers
  },
  data() {
    return {
      transfers: [
        {id:"12345", picture: "rebeca.jpg", name: "Rebeca Moore", date: "20 january 2019", amount: 972},
        {id:"123456", picture: "rebeca.jpg", name: "Franz Ferdinand", date: "19 january 2019", amount: 150},
        {id:"1234567", picture: "rebeca.jpg", name: "John Doe", date: "19 january 2019", amount: 972},
      ]
    }
  },
};
</script>

