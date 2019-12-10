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
                ds:[], 
                l:[],     
                
            }
  },
  mounted () {
    axios
    .get('https://api.github.com/repos/obrienam/CV_Research/languages')
    .then(response => {
        this.data=response.data
        this.processData()
        this.renderChart({
            labels: ["Python"],
            datasets: [
                {
                label: 'Language Distribution',
                backgroundColor: ["#41B883"],
                data: this.ds
                }
            ]
        })
    });
   
  },
  methods: {
      processData: function () {
        this.ds.push(this.data["Python"])
        
      }
  }
}
</script>
<style scoped>

</style>