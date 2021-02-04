<template>
  <v-container>      
    <v-layout row wrap>
      <v-flex xs12 mt-3 justify-center>
        <v-divider></v-divider>
        <v-data-table
            :headers="headers"
            :items="training" 
            hide-default-footer
            :mobile-breakpoint="600"
          >
          <template v-slot:[`item.action`]="{ item }">
            <span>
              <router-link :to="{ name: 'Form', params:{ training_id:item.id }}">
                <v-icon small class="mr-2">fas fa-edit</v-icon>
              </router-link>
              <v-icon small class="mr-2" @click="deleteConfirm(item.id)">mdi-delete</v-icon>
            </span>
          </template>
          <template v-slot:[`item.part`]="{ item }">
            <v-chip
              :color="getColor(item.part)"
              dark
            >
              {{ item.part }}
            </v-chip>
          </template>
        </v-data-table>
      </v-flex>
    </v-layout>
  </v-container>
</template>


<script> 
import {mapActions} from 'vuex'
export default {
  created(){
    this.training = this.$store.state.trainingMenu
  },
 
  data () {
    return {
      headers: [
        {
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: '種目', value: 'menu' , sortable:false},
        { text: '部位', value: 'part' , sortable:false},
        { text: '回数', value: 'reps' , sortable:false},
        { text: '重量 (kg)', value: 'weight' , sortable:false},
        { text: 'セット数', value: 'sets', sortable:false },
        { text: '編集' , value:'action', sortable:false },
      ],
      training: [],
    }
  },
  methods:{
     getColor (part) {
        if (part  === '胸') return 'red'
        else if (part === '肩') return 'orange'
        else if (part === '腕') return 'green'
        else if (part === '背中') return 'blue'
        else if (part === '脚') return 'black'
        else return 'yellow'
      },

    deleteConfirm(id){
      if(confirm('削除してもよろしいですか？')){
        this.deleteTraining({id})
        
      }
    },
    ...mapActions(['deleteTraining'])
  }
}
</script>
<style scoped lang="scss">
a {
  text-decoration: none;
}

</style>

