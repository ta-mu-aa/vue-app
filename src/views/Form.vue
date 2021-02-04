<template>
  <v-flex>
    <v-card class ="pa-3 pb-6">
      <v-card-text>
        <v-form lazy-validation ref = "form">
          <v-container>
            {{$store.state.trainingDay}}
            <v-row>
              <v-col
                cols="12"
                md="3"
                xs="7"
              >
                <v-text-field
                  label="種目"
                  :rules="nameRules"
                  required
                  v-model="menu.menu"
                ></v-text-field>
              </v-col>
              <v-col
                cols="6"
                md="2"
              >
                <v-select
                  :items="parts"
                  label="部位"
                  v-model="menu.part"
                ></v-select>
              </v-col>

              <v-col
                cols="6"
                md="2"
              >
                <v-text-field
                  label="重量"
                  required
                  v-model="menu.weight"
                  type="number"
                ></v-text-field>
              </v-col>

              <v-col
                cols="6"
                md="2"
              >
                <v-text-field
                  label="回数"
                  required
                  v-model="menu.reps"
                  type="number"
                ></v-text-field>
              </v-col>
              <v-col
                cols="6"
                md="2"
              >
                <v-text-field
                  label="セット数"
                  required
                  v-model="menu.sets"
                  type="number"
                ></v-text-field>
              </v-col>
            </v-row>
              <v-btn small pa-3 class="ml-2 float-left" :to="{name: 'Record'}" >戻る</v-btn>
              <v-btn color="info" class="ml-2 float-right"  v-on:click.stop="submit">追加</v-btn>
          </v-container>
        </v-form>
      </v-card-text>
    </v-card>
  </v-flex>
</template>

<script>
import {mapActions} from 'vuex'
  export default {
    name: 'Form',
    created(){
      if(!this.$route.params.training_id) return
    
      const training = this.$store.getters.getTrainingId(this.$route.params.training_id)
      if(training){
        this.menu = training
      }else{
        this.$router.push({name: ('Record')})
      }
    },
    data(){
      return{
        menu:{date:this.$store.state.trainingDay},
        parts:['胸','肩','腕','背中','脚','腹'],
        nameRules:[
           v => !!v || '種目を入力してください',
          v => (v && v.length > 0) || '種目を入力してください',
        ]
      }
    },
    methods:{
      submit(){
        if(this.$refs.form.validate()){
          if(this.$route.params.training_id){
            this.updateTraining({id: this.$route.params.training_id, menu: this.menu})
          }else{
            this.addTrainingMenu(this.menu)
          }
          this.$router.push({ name: 'Home'})
          this.training = {}
          }
      },

      ...mapActions(['addTrainingMenu','updateTraining','setDay'])
    }
  }
    
</script>

<style>
</style>
