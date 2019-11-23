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
      <b-tab-item label="Cryptocurrency">
      <nav class="breadcrumb" aria-label="breadcrumbs">
      <ul>
        <li><a href="#">Home</a></li>
        <li class="is-active"><a href="#" aria-current="page">Cryptocurrency</a></li>
      </ul>
      </nav>
      <div class="tile is-ancestor">
        <div class="tile is-parent">
          <div class="tile is-child box">
            <p class="title">Cryptocurrency</p>
              <img src="../public/img/logo.png" class="bcoin">
            
          </div> 
        </div>
        
        <div class="tile is-5 is-vertical is-parent">
        <div class="tile is-child box">
          <cointable/>
        </div>
        <div class="tile is-child  box">
          <cointable/>
            </div>
        </div>
        
      </div>
      
      
      </b-tab-item> 
      <b-tab-item label="Thingsboard">
      <nav class="breadcrumb" aria-label="breadcrumbs">
      <ul>
        <li><a href="#">Home</a></li>
        <li class="is-active"><a href="#" aria-current="page">Thingsboard</a></li>
      </ul>
      </nav>
      </b-tab-item>
      <b-tab-item label="Table Experiments">
        <nav class="breadcrumb" aria-label="breadcrumbs">
        <ul>
          <li><a href="#">Home</a></li>
          <li class="is-active"><a href="#" aria-current="page">Table Experiments</a></li>
        </ul>
        </nav>
        <h1>Test Data</h1>
          <datatable/>
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

Vue.use(Buefy, axios,cointable,{
  defaultIconPack: "fa"
})
export default {
  name: 'app',
  components:{
    cointable
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
  height:70%
}
</style>
