<template>
<center>
  <div>
    <div class="jumbotron">
      <h1>Dashboard</h1>
    </div>
    <div id="card">
      <b-card no-body class="overflow-hidden" style="max-width: 540px;">
        <center>
          <b-card-img  id ="image" :src="require('assets/user.png')" class="rounded-0"></b-card-img>
          <b-row no-gutters>
            <b-card-body>
              <h1>HI {{firstname}}</h1>
              <h3>Welcome to JM APP</h3>
            </b-card-body>
          </b-row>
        </center>
      </b-card>
    </div>
  </div>
</center>
</template>

<style scoped>
#card {
  margin-top: 0;
  height: 20px;
}
.jumbotron{
    padding:15px;
}
#image {
  width: 250px;
  height: 220px;
}
</style>

<script>
// import ROUTER from "router";
export default {
  name: "card",
  data() {
    return {
      firstname: sessionStorage.getItem("Firstname")
    };
  },
};
</script>

