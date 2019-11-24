<template>
    <div id="cointable">
        <p class="title">Bitcoin Value</p>
          <b-table :data="dbcoin" :columns="columns" backend-sorting backend-pagination></b-table>
    </div>
</template>

<script>
import 'buefy/dist/buefy.css'
import Vue from 'vue'
import Buefy from 'buefy'
import 'font-awesome/css/font-awesome.min.css'
import axios from 'axios'
import Component from "vue-class-component"

Vue.use(Buefy, axios,{
  defaultIconPack: "fa"
})

@Component 
class datatable extends Vue{
    
  err=false;
  dbcoin=[]; 
  dusd=[];
  dgb=[];
  deur=[];
  //isPaginated= true; isPaginationSimple: false;paginationPosition: 'bottom', perPage: 5, currentPage: 1
  columns=[
    {
      field:"rate",
      label:"Exchange Rate",
    },
    {
      field:"description",
      label:"Currency",
    }
  ];
  mounted () {
      axios
      //.get('http://35.172.221.32:1026/v2/entities')
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => {
        this.dusd = response.data.bpi.USD;
        this.dgb = response.data.bpi.GBP;
        this.deur = response.data.bpi.EUR;
        this.dbcoin.push(this.dusd)
        this.dbcoin.push(this.dgb)
        this.dbcoin.push(this.deur)
      })
      
  }

} export default datatable;
</script>
<style scoped>
#fiware_datatable {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.pagination-list a{
  background-color: rgb(255,210,4);
}

.pagination-list a.is-current{
  background-color: rgb(255,210,4);
  color:black;
  border-color:black
}
.pagination-list a:active{
  border-color:black
}
a.pagination-link.pagination-next:active{
  border-color:black
}
a.pagination-link.pagination-previous:active{
  border-color:black
}
</style>