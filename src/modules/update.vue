<template>

<div class="row loginPage">
      <div class="col-md-4"></div>
      <div class="col-md-4">
        <div class="container">
          <div class="card">
            <div class="card-header">UPDATE INFO</div>
            <div class="card-body">
              <b-col md="6">
            <b-card-img id="pic1" class="rounded-0"></b-card-img>
            <div class="pic">
              <label>Change profile</label>
              <input v-model="profile" placeholder="enter image url"/>
            </div>
          </b-col>
                <div class="form-group">
                <label for="username" class="bmd-label-floating">Username</label>
                <input
                    type="text"
                    class="form-control"
                    id="username"
                    v-model="username"
                />
              </div>
              <div class="form-group">
                <label for="email" class="bmd-label-floating">Email</label>
                <input
                  type="text"
                  class="form-control"
                  id="email"
                  v-model="email"
                />
              </div>
              <div class="form-group">
                <label for="pwd" class="bmd-label-floating">Password</label>
                <input
                  type="password"
                  class="form-control"
                  id="passw"
                  v-model="password"
                />
              </div>
              <center>
                <button type="button" class="btn btn-outline-success login-btn" id="btnLogin" @click='save'>Save changes</button>
                
              </center>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import ROUTER from "router"

import AUTH from 'services/auth'
export default {
  data() {
    AUTH
    return {
      username: "",
      email: "",
      password: "",
      profile:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTugznlxaKe8PmdqZIN3dtOI2Iktd_cXtfwo6YpDGnImSk7qCDJ7w"
    };
  },
  methods: {
    save: function(e) {
      e.preventDefault();
      sessionStorage.setItem("Firstname", this.username),
      sessionStorage.setItem("Email", this.email),
      sessionStorage.setItem("Password", this.password),
      sessionStorage.setItem(" Change profile", this.profile),
      AUTH.save(this.username,this.email, this.password, this.profile)
      let user = AUTH.login(this.email, this.password);

      AUTH.setUser(user);
              if(user != null){
                ROUTER.push('/Dashboard');
              }

    

  },
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

.pic{
  position:absolute;
  left:100%;
  top: 20px;
  
}

</style>
