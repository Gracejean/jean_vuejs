<template>
  <center>
  <div id="container">
    <div class="jumbotron">
      <h1>Personal Information</h1>
    </div>
    <div id="card">
      <b-card no-body class="overflow-hidden" style="max-width: 540px;">
        <b-row no-gutters>
          <b-col md="6">
            <b-card-img :src="require('assets/user.png')" class="rounded-0">{{profile}}</b-card-img>
          </b-col>
          <b-col md="6">
            <b-card-body title="Personal Info">
                <hr>
              <b-card-text>
                <h6>Username: {{firstname}}</h6>
                <h6>Email: {{email}}</h6>
                <h6 type="password">Password: {{password}}</h6>
              </b-card-text>
              <button @click = "update()">Update</button>

            </b-card-body>
          </b-col>
        </b-row>
      </b-card>
    </div>
  </div>
  </center>
</template>

<style>
.jumbotron{
    padding: 15px;
}
#card {
  margin-top: 50px;
}
</style>
<script>
import ROUTER from "router"

import AUTH from 'services/auth'

export default {
  name: "container",
  data() {
    return {
      firstname: sessionStorage.getItem("Firstname"),
      email: sessionStorage.getItem("Email"),
      password: sessionStorage.getItem("Password"),
      profile: sessionStorage.getItem("Profile")
    };
  },
  methods:{
    update: function(){
      AUTH.update(this.firstname,this.email, this.password,this.profile)
      let user = AUTH.login(this.email, this.password);

      AUTH.setUser(user);
              if(user != null){
                ROUTER.push('/update');
              }

    }
  }
};
</script>
