<template>
  <div id="app">
    <b-navbar>
      <template slot="brand">
        <b-navbar-item>
          <img src="../public/img/asu.png">
        </b-navbar-item>
      </template>
    <template slot="start">
      <b-navbar-item href="#">
        Dashboard
      </b-navbar-item>
    </template>
    </b-navbar>
    <div id="page-wrap">
    <b-tabs type="is-toggle" position="is-centered" mobile-burger="true" left="true" >
      <b-tab-item label="Bitcoin Price Index">
      <nav class="breadcrumb" aria-label="breadcrumbs">
      <ul>
        <li><a href="#">Home</a></li>
        <li class="is-active"><a href="#" aria-current="page">Bitcoin Price Index</a></li>
      </ul>
      </nav>
      <div class="tile is-ancestor">
        <div class="tile is-parent">
          <div class="tile is-child box">
            <p class="title">Bitcoin Price Index</p>
              <img src="../public/img/logo.png" class="bcoin">
      
          </div> 
        </div>
        
        <div class="tile is-8 is-vertical is-parent">
        
        <div class="tile is-child  box">
          <p class="title">Value Over Time</p>
          <b-tabs position="is-centered">
            <b-tab-item label="USD">
              <hiscoinUSD/>
            </b-tab-item>
            <b-tab-item label="EUR">
              <hiscoinEUR/>
            </b-tab-item>
            <b-tab-item label="GPB">
              <hiscoinGPB/>
            </b-tab-item>
          </b-tabs>
          <test/>
            </div>
        </div>
        
      </div>
      <div class="tile is-ancestor">
            <div class="tile is-parent">
              <div class="tile is-child box">
                  <cointable/>
              </div> 
            </div>
      </div>
      
      </b-tab-item> 
      <b-tab-item label="GitHub">
        <nav class="breadcrumb" aria-label="breadcrumbs">
        <ul>
          <li><a href="#">Home</a></li>
          <li class="is-active"><a href="#" aria-current="page">GitHub</a></li>
        </ul>
        </nav>
          <div class="tile is-ancestor">
          <div class="tile is-parent">
            <div class="tile is-child box">
              <p class="title">GitHub</p>
                <img src="../public/img/Gitlogo.png" class="bcoin">
        
            </div> 
          </div>
          
          <div class="tile is-8 is-vertical is-parent">
          <div class="tile is-child box">
            <b-tabs position="is-centered">
              <b-tab-item label="Honors-Thesis">
                <gitChartht/>
              </b-tab-item>
              <b-tab-item label="Vue_Dashboard">
                <gitChartvd/>
              </b-tab-item>
              <b-tab-item label="CV_Research">
                <gitChartcvr/>
              </b-tab-item>
            </b-tabs>
          </div>
            
          </div>
          
      </div>
        
      <div class="tile is-ancestor">
            <div class="tile is-parent">
              <div class="tile is-child box">
                <p class="title">Commit History</p>
                  <gitTable/>
              </div> 
            </div>
            
            </div>
          </b-tab-item>
        
        </b-tabs>  
        </div>

      </div>
  
</template>

<script>
import 'buefy/dist/buefy.css'
import Vue from 'vue'
import Buefy from 'buefy'
import 'font-awesome/css/font-awesome.min.css'
import axios from 'axios'
import cointable from './components/datatable.vue'
import hiscoinUSD from './components/hiscoinUSD.vue'
import hiscoinEUR from './components/hiscoinEUR.vue'
import hiscoinGPB from './components/hiscoinGPB.vue'
import gitTable from './components/gitTable.vue'
import gitChartvd from './components/gitChartvd.vue'
import gitChartht from './components/gitChartht.vue'
import gitChartcvr from './components/gitChartcvr.vue'
Vue.use(Buefy, axios,cointable,hiscoinUSD,hiscoinEUR,hiscoinGPB,gitTable,gitChartvd,gitChartht,gitChartcvr,{
  defaultIconPack: "fa"
})
export default {
  name: 'app',
  components:{
    cointable,
    hiscoinUSD,
    hiscoinEUR,
    hiscoinGPB,
    gitTable,
    gitChartvd,
    gitChartht,
    gitChartcvr,
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

/* Beginnings of a dark mode that follows the system setting.
@media (prefers-color-scheme: dark) {
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: white;
    background-color:black;
    margin-top: 60px;
  } 
}*/

img {
  width: 100%;
  height: 100%
}
.tabs.is-toggle li.is-active a{
  background-color: rgb(255,210,4);
  border-color:black;
  color: black
}
.tabs li.is-active a{
  color: black;
  border-color:black;
}
.navbar-menu a{
  color:black!important;
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
.breadcrumb li a{
  color:gray
}
.breadcrumb li.is-active a{
  color:black
}
img.bcoin{
  height:60%
}
</style>
