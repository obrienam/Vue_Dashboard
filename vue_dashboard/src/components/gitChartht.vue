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
    .get('https://api.github.com/repos/obrienam/Honors-Thesis/languages')
    .then(response => {
        this.data=response.data
        this.processData()
        this.renderChart({
            labels: ["Python","Shell"],
            datasets: [
                {
                label: 'Language Distribution',
                backgroundColor: ["#41B883", "#E46651"],
                data: this.ds
                }
            ]
        })
    });
   
  },
  methods: {
      processData: function () {
        this.ds.push(this.data["Python"])
        this.ds.push(this.data["Shell"])
      }
  }
}
</script>
<style scoped>

</style>