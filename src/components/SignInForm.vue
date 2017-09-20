<template>
  <div class="signInPage">
    <form @submit.prevent="signIn">
      <div class="row">
        <lable>用户名</lable>
        <input type="text" required v-model="formData.username">

      </div>
      <div class="row">
        <label>密码</label>
        <input type="password" required v-model="formData.password">
      </div>
      <div class="actions">
        <input type="submit" value="提交">
        <span>{{errorMessage}}</span>
      </div>
    </form>
  </div>
</template>


<script>
  import AV from '../lib/leancloud'
  import getErrorMessage from '../lib/getErrorMessage'
  import getAVUser from '../lib/getAVUser'

  export default {
    name:'SignInForm',
    data(){
      return{
        formData:{
          username:'',
          password:''
        },
        errorMessage:''
      }
    },
    methods:{
      signIn(){
        let {username,password}=this.formData
      AV.User.logIn(username,password).then(()=>{
          this.$emit('success',getAVUser())
      },(error)=>{
          this.errorMessage=getErrrorMessage(error)
      })
    }
  }
  }

</script>

<style scoped>





</style>


















