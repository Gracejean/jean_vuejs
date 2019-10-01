<template>
  <div class="row registerPage">
      <div class="col-md-4"></div>
      <div class="col-md-4">
        <div class="container">
          <center>
            <b-card-img id="image1" :src="require('assets/img.png')" class="rounded-0"></b-card-img>
            </center>
          <div class="card">
            <div class="card-header">REGISTER</div>
            <div class="card-body">
                <div class="form-group">
                <label for="fname" class="bmd-label-floating">Firstname</label>
                <input
                  type="text"
                  class="form-control"
                  id="fname"
                  v-model = "content.firstname"
                  placeholder="Enter your firstname.."
                />
              </div>
              <div class="form-group">
                <label for="lname" class="bmd-label-floating">Lastname</label>
                <input
                  type="text"
                  class="form-control"
                  id="lname"
                  v-model = "content.lastname"
                  placeholder="Enter your lastname.."
                />
              </div>
              <div class="form-group">
                <label for="email" class="bmd-label-floating">Email</label>
                <input
                  type="email"
                  class="form-control"
                  id="email"
                  v-model= "content.email"
                  placeholder="Enter your email.."
                />
              </div>
              <div class="form-group">
                <label for="pass" class="bmd-label-floating">Password</label>
                <input
                  type="password"
                  class="form-control"
                  id="pass"
                  v-model = "content.password"
                  placeholder="Enter your password.."
                />
              </div>
                            <div class="form-group">
                <label for="cpass" class="bmd-label-floating">Confirm Password</label>
                <input
                  type="password"
                  class="form-control"
                  id="cpass"
                  v-model = "content.cpassword"
                  placeholder="Confirm you password.."
                />
              </div>
              <center>
                <button type="button" class="btn btn-outline-success register-btn" id="btnRegister" @click = "submit">Register</button>

                <br>
                <p>Already have an account?</p>
                <router-link to="/Login">Login</router-link>
              </center>
            </div>
          </div>
        </div>
      </div>
    </div>


</template>
<style scoped lang="scss">
</style>
<script>
import AUTH from "services/auth";
export default {
  data() {
    return {
      auth: AUTH,
      content: {
        firstname: "",
        lastname: "",
        email: "",
        password: "",
        cpassword: ""
      }
    };
  },
  methods: {
    submit: function(e) {
      e.preventDefault();
        sessionStorage.setItem("Firstname", this.content.firstname),
        sessionStorage.setItem("Lastname", this.content.lastname),
        sessionStorage.setItem("Email", this.content.email),
        sessionStorage.setItem("Password", this.content.password),
        AUTH.register(this.content.email, this.content.password);
    }
  }
};
</script>

<style>
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

#btnRegister {
  color: black;
  border: 2px solid black;
  margin-top: 5px;
  padding: 12px 30px;
}

.container {
  background-color:white;
  padding: 10px;
  margin-top:50px;
  
}

#image1 {
  height: 150px;
  width: 150px;
  position: absolute;
  top:10px;
  left: 190px;
  z-index: 1;
}

</style>

