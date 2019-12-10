<template>
<div id=gitTable>
    <b-tabs position="is-centered">
      
        <b-tab-item label="Honors-Thesis">
          <b-table :data="gdata" :columns="columns" paginated :per-page="5" backend-sorting></b-table>
        </b-tab-item>  
        <b-tab-item label="Vue_Dashboard">
          <b-table :data="gdata2" :columns="columns" paginated :per-page="5" backend-sorting></b-table>
        </b-tab-item>  
        <b-tab-item label="Steminar-Duck-Game">
          <b-table :data="gdata3" :columns="columns" paginated :per-page="5" backend-sorting></b-table>
        </b-tab-item>  
        <b-tab-item label="CV_Research">
          <b-table :data="gdata4" :columns="columns" paginated :per-page="5" backend-sorting></b-table>
        </b-tab-item>  
    </b-tabs>
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
                gdata:[],
                gdata2:[],
                gdata3: [],
                gdata4:[],
                defaultSortDirection: 'asc',
                sortIcon: 'arrow-up',
                sortIconSize: 'is-small',
                columns:[
                {
                field:"name",
                label:"User",
                searchable:true,
                narrowed:true
                },
                {
                field:"date",
                label:"Date",
                searchable:true,
                narrowed:true
                
                },
                {
                field:"message",
                label:"Comment",
                searchable:true,
                narrowed:true
           
                }
            ]
            }
            
  },
  mounted () {
    axios
    .get('https://api.github.com/repos/obrienam/Honors-Thesis/commits')
    .then(response => {
        this.data=response.data
        this.processData(this.gdata)
    });
    axios
    .get('https://api.github.com/repos/obrienam/Vue_Dashboard/commits')
    .then(response => {
        this.data=response.data
        this.processData(this.gdata2)
    });
    axios
    .get('https://api.github.com/repos/obrienam/Steminar-Duck-Game/commits')
    .then(response => {
        this.data=response.data
        this.processData(this.gdata3)
    });
    axios
    .get('https://api.github.com/repos/obrienam/CV_Research/commits')
    .then(response => {
        this.data=response.data
        this.processData(this.gdata4)
    });
   
  },
  methods: {
      processData: function (d) {
        var i;
        for (i=0;i < this.data.length; i++) {
        this.data[i].commit.author.message=this.data[i].commit.message
        d.push(this.data[i].commit.author)
        }
        
      }
     
  }
}
</script>
<style scoped>

</style>