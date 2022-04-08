<template>
  <div class="vue-tempalte">
    <form @submit.prevent="handleSubmit">
      <h3>Sign In</h3>

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
        Sign In
      </button>
</div>
      

      <p class="forgot-password text-right mt-2 mb-4">
        <router-link to="/forgot-password">Forgot password ?</router-link>
      </p>

   
    </form>
  </div>
</template>

<script>
  const CryptoJS = require("crypto-js")

export default {
  data() {
    return {
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
      console.log(this.email,this.password);
if (this.email && this.password) {
  var data=JSON.parse(localStorage.getItem('data'));
  console.log(data,this.email,this.password);
  if (this.email===this.decrypt(data['email'])&&this.password===this.decrypt(data['password'])) {
     this.$alert("Successfully Logged in","Login Success",'success') 
  }
  else{
      this.$alert("Authentication failed","Login Error",'error')

  }
}
else{
      this.$alert("Error while login Please try again","login Error",'error')

}
    }
  }
};
</script>
