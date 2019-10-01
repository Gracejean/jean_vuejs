<template>
  <div class="row loginPage">
      <div class="col-md-4"></div>
      <div class="col-md-4">
        <div class="container">
          <center>
            <b-card-img id="image1" :src="require('assets/img.png')" class="rounded-0"></b-card-img>
            </center>
          <div class="card">
            <div class="card-header">LOGIN</div>
            <div class="card-body">
              <div class="form-group">
                <label for="email" class="bmd-label-floating">Email</label>
                  <input type="text" class="form-control" id="email" v-model="email" placeholder="Enter email..."/>
                
              </div>
              <div class="form-group">
                <label for="pwd" class="bmd-label-floating">Password</label>
                <input
                  type="password"
                  class="form-control"
                  id="passw"
                  v-model="password"
                  placeholder="Enter password..."
                />
              </div>
              <center>
                <button type="button" class="btn btn-outline-success login-btn" id="btnLogin" @click='submit'>Login</button>
                
              </center>
            </div>
          </div>
        </div>
      </div>
    </div>

  </template>
<style scoped lang="scss">
@import "assets/colors.scss";

#username {
  color: $primary !important;
}
#pass {
  color: $primary !important;
}
</style>
<script>
import AUTH from 'services/auth'
import jquery from 'jquery'
export default {
  data() {
    AUTH
    return {
      email: null,
      password: null,
      config: CONFIG
    };
  },
  methods: {
    redirect(params){
      aler('hi')
      ROUTER.push(params)
    },
    
    test(){
      let link = 'http://localhost:3000'
      jquery.ajax({
        url:link,
        method: "POST",
        headers:{
          'Access.Control.Allow.Origin':'*'
        }
      })
    },
    // login(){
    //   console.log('hi')
    //   jquery.get('http://localhost:300').then(response =>{
    //     console.log(response)
    //   })
    // }

  },
  computed:{

  }
};
</script>

<style scoped>
  .card {
  background-color: pink;
  margin-top: 50px;
  padding: 30px;
  
}
  

.h3 {
  margin-left: 500px;
  margin-top: 300px;
  font-size: 40px;
  font-family: Times new;
}
.nav {
  margin-block: auto;
}

.card-header {
  text-align: center;
  font-weight:bold;
  font-size: 30px;
  letter-spacing: 5px;
  background-color: black;
  color:pink;
  
}
.container {
  background-color: white;
  padding: 10px;
  margin-top:50px;
  
}

label {
  font-weight:bold;
}

input {
  border: 2px solid black;
}

#btnLogin {
  color: black;
  border: 2px solid black;
  margin-top: 5px;
  padding: 12px 30px;
}
#image1 {
  height: 150px;
  width: 150px;
  position: absolute;
  top:13px;
  left: 38%;
  z-index: 1;
}

</style>

