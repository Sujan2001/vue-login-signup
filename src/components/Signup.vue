
<template>
  <div class="vue-tempalte">
    <form @submit.prevent="handleSubmit">
      <h3>Sign Up</h3>

      <div class="form-group">
        <label>Full Name</label>
        <input type="text" v-model="fullname" class="form-control form-control-lg" required />
      </div>

      <div class="form-group">
        <label>Email address</label>
        <input type="email" v-model="email" class="form-control form-control-lg" required />
      </div>

      <div class="form-group">
        <label>Password</label>
        <input type="password" v-model="password" class="form-control form-control-lg" required />
      </div>
<div class="button-div">

      <button type="submit" class="btn btn-dark btn-lg btn-block">
        Sign Up
      </button>
</div>

      <p class="forgot-password text-right">
        Already registered
        <router-link :to="{ name: 'login' }">sign in?</router-link>
      </p>
    </form>
  </div>
</template>

<script>
const CryptoJS = require("crypto-js")

export default {
    data() {
    return {
      fullname:null,
      email:null,
      password:null
    };
  },
  methods:{
    encrypt (src) {
    const passphrase = '123456'
    return CryptoJS.AES.encrypt(src, passphrase).toString()
  },

  decrypt (src) {
    const passphrase = '123456'
    const bytes = CryptoJS.AES.decrypt(src, passphrase)
    const originalText = bytes.toString(CryptoJS.enc.Utf8)
    return originalText
  },
    handleSubmit(){
if (this.email && this.password&&this.fullname) {
  localStorage.setItem('data',JSON.stringify({fullname:this.encrypt(this.fullname),email:this.encrypt(this.email),password:this.encrypt(this.password)}));
  this.$alert("Successfully Signed up","Sign Up Success",'success')
}
else{
    this.$alert("Error while sign up Please try again","Signup Error",'error')

}
    
    }
  }
};
</script>
