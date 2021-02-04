<template>
  <div>
    <h1>部位別週間セット数</h1>
    
    <p>この日から一週間</p>
    <Chart/>
  </div>
</template>

<script>
import Chart from '@/components/Chart';

export default {
  components: {
    Chart,
  },
  data(){
    return{
      week:'',
    }
  }
}

</script>