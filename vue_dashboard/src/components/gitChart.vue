<template>
    <div id="gitChart">
      
      <gitChartvd/>
    </div>
</template>
<script>
import 'buefy/dist/buefy.css'
import Vue from 'vue'
import Buefy from 'buefy'
import 'font-awesome/css/font-awesome.min.css'
import axios from 'axios'
import Component from "vue-class-component"
import gitChartvd from "./gitChartvd.vue"
Vue.use(Buefy, axios,gitChartvd,{
  defaultIconPack: "fa"
})

@Component 
class gitChart extends Vue{
  
 
  err=false;
  alldata=[];
  vdata1=[];
  
  vdata2=[];
  //isPaginated= true; isPaginationSimple: false;paginationPosition: 'bottom', perPage: 5, currentPage: 1
  columns=[
    {
      field:"name",
      label:"User",
    },
    {
      field:"date",
      label:"Date",
    },
    {
      field:"message",
      label:"comment"
    }
  ];
  mounted () {
      axios
      .get('https://api.github.com/repos/obrienam/Vue_Dashboard/commits')
      .then(response => {
        this.vdata1.push(response.data[0].commit.author)
        this.vdata2.push(response.data[0].commit.message)
        this.vdata1.push(this.vdata2[0])
      })
      
  }
  
  

} export default gitChart;
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