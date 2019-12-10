<script>

import axios from 'axios'
import { Doughnut } from 'vue-chartjs'
import Vue from 'vue'
Vue.use(axios,Doughnut,{
  defaultIconPack: "fa"
})
export default {
  extends: Doughnut,
  data() {
            return {
                data:[], 
                ds:[], 
                l:[],     
                
            }
  },
  mounted () {
    axios
    .get('https://api.github.com/repos/obrienam/Vue_Dashboard/languages')
    .then(response => {
        this.data=response.data
        this.processData()
        this.renderChart({
            labels: ["Vue","HTML","JavaScript"],
            datasets: [
                {
                label: 'Language Distribution',
                backgroundColor: ["#41B883", "#E46651", "#00D8FF"],
                data: this.ds
                }
            ]
        })
    });
   
  },
  methods: {
      processData: function () {
        this.ds.push(this.data["Vue"])
        this.ds.push(this.data["HTML"])
        this.ds.push(this.data["JavaScript"])
      }
  }
}
</script>
<style scoped>

</style>