<template>
  <v-app>
    <v-container text-center justify-center >
      <v-layout row wrap  align-content="center">
        <v-flex xs12 mt-4>
          <v-btn  v-on:click="login">
            <img src="../assets/google.logo.jpg" width="20" >Googleアカウントをお持ちの方</v-btn>
        </v-flex> 
      </v-layout>
    </v-container>
    <v-container text-center justify-center>
      <v-card width="400" class="mx-auto mt-5">
        <v-card-title>
          <h1 class="display-1">ログイン</h1>
        </v-card-title>
        <v-card-text>
          <v-form v-on:submit.prevent="addmail" ref="form">
            <v-text-field  
            prepend-icon="mdi-account-circle" 
            label="メールアドレス" 
            v-model="email"
            :rules="emailRules"
            />
            <v-text-field 
            v-bind:type="showPassword ? 'text' : 'password'" 
            prepend-icon="mdi-lock" 
            v-bind:append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'" 
            label="パスワード" 
            :rules="passwordRules"
            @click:append="showPassword = !showPassword"
            v-model="password" 
            />
              <v-card-actions class="justify-end" >
                <v-btn color="info" type="submit" @click="validate">ログイン</v-btn>
              </v-card-actions>
          </v-form>
        </v-card-text>
      </v-card>
      <p style= padding-top:50px; >初めての方は<router-link :to="{name:'signIn'}">こちら</router-link></p>
    </v-container>
  </v-app>
</template>

<script>
import {mapActions} from 'vuex'
import firebase from "firebase"
import "firebase/auth";
export default{
  data(){
    return{    
      emailRules:[
        v => !!v || 'メールアドレスを入力してください',
        v => /.+@.+\..+/.test(v) || '有効なメールアドレスを入力してください',],
      passwordRules:[
        v => !!v || 'パスワードを入力してください',
        v => (v && v.length >= 6) || '6桁以上の安全なパスワード',],
      showPassword: false,
      email:'',
      password:'',
    }
  },
  methods:{
    addmail(){
      firebase.auth().signInWithEmailAndPassword(this.email,this.password)
      .catch(function(){
        console.log("error")
        alert('このアカウントは登録されていません')
      })
    },
    validate () {
      this.$refs.form.validate()
    },
    ...mapActions(['login'])
  }
}
</script>
