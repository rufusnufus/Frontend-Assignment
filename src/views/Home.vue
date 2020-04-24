<template>
  <v-container
    fluid
    fill-height
  >
    <v-layout align-center justify-center row fill-height>
      <v-data-table
          :headers="headers"
          :items="currencies"
          :items-per-page="10"
          :loading="loading"
          class="elevation-1"
          id="mytable"
      ></v-data-table>
    </v-layout>
  </v-container>
</template>

<script>

export default {
  name: "Home",
  data(){
    return {
      timer: "",
      loading: true,
      headers: [
        {
          text: "Currency",
          value: "currency",
          align: "start",
          sortable: false,
        },
        {
          text: "Rate",
          value: "rate",
          align: "left",
          sortable: false,
        }
      ],
      currencies: [],
    }
  },
  mounted: function(){
    this.getData(this);
  },
  methods: {
    getData : async(vm) => {
      const response = await fetch(process.env.VUE_APP_API_URL);
      if(!response.ok) return;
      const json = await response.json();
      vm.loading = false;
      vm.currencies = [];
      for(let key in json.rates){
        vm.currencies.push({currency:key, rate: json.rates[key]});
      }
    },
  },
};
</script>

<style>
#mytable table thead th{
  background-color: #00909e;
  color: white;
}
</style>
