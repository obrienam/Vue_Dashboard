
<script>

import axios from 'axios'
import { Bar } from 'vue-chartjs'
import Vue from 'vue'
Vue.use(axios,Bar,{
  defaultIconPack: "fa"
})
export default {
  extends: Bar,
  data() {
            return {
                ds:[], 
                l:[],     
                
            }
  },
  mounted () {
    axios
    .get('https://api.coindesk.com/v1/bpi/historical/close.json')
    .then(response => {
        this.data=response.data.bpi
        this.processDate()
        this.renderChart({
            labels: this.l,
            datasets: [
                {
                label: 'Bitcoin Value in USD',
                backgroundColor: '#f87979',
                data: this.ds
                }
            ]
        })
    });
   
  },
  methods: {
      processDate: function () {
        for (var date in this.data) {
        this.ds.push(this.data[date])
        this.l.push(date)
        }

      }
  }
}
</script>
<style scoped>

</style>