<template>
<div id=gitThesis>
  
    <b-table :data="gdata1" :columns="columns" backend-sorting backend-pagination></b-table>
</div>
</template>
<script>

import axios from 'axios'
import 'buefy/dist/buefy.css'
import Buefy from 'buefy'
import 'font-awesome/css/font-awesome.min.css'
import Vue from 'vue'
Vue.use(axios,Buefy,{
  defaultIconPack: "fa"
})
export default {
  data() {
            return {
                alldata:[],  
                gdata1:[],
                gdata2:[], 
                gdata:[],  
                l:[],     
                columns:[
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
            ]
            }
            
  },
  mounted () {
    axios
    .get('https://api.github.com/repos/obrienam/Honors-Thesis/commits')
    .then(response => {
        this.data=response.data
        this.processData()
    });
   
  },
  methods: {
      processData: function () {
        var i;
        for (i=0;i < this.data.length; i++) {
        this.data[i].commit.author.message=this.data[i].commit.message
        this.gdata1.push(this.data[i].commit.author)
        this.gdata2.push(this.data[i].commit.message)
        
        }
        
      }
     
  }
}
</script>
<style scoped>

</style>