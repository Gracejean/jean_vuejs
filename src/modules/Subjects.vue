<template>
  <center>
    <div>
      <div class="jumbotron">
        <h1>Subjects</h1>
      </div>
      <div class="scroll">
        <center>
          
        <b-card text-align id="card" img-top tag="article" style="max-width: 30rem;" class="mb-2">
          <b-form-group label-size="lg" label-for="input-lg">
            <label id="Subject">Subject:</label>
            <b-form-input v-model="infos.subject" id="subject" size="lg"></b-form-input>
            <label id="teacher">Teacher:</label>
            <br />
            <b-form-input v-model="infos.teacher" id="teacher" size="lg"></b-form-input>
            <br />
            <label id="time">Schedule:</label>
            <b-form-input v-model="infos.schedule" id="time" size="lg"></b-form-input>
            <br />
            <b-button variant="primary" @click="addItem">Add Subject</b-button><br><br>
            <label id="time">Delete:</label>
            <b-form-input v-model="infos.del" id="time" size="lg"></b-form-input>
            <br />
            <b-button id="del" @click="deleteItem">Delete Subject</b-button>
            <br />
            <br />
            <mdb-scrollbar height="200px">
              <mdb-tbl bordered>
                <mdb-tbl-head color="light">
                  <tr>
                    <th scope="col">Subject</th>
                    <th scope="col">Teacher</th>
                    <th scope="col">Schedule</th>

                  </tr>
                </mdb-tbl-head>
                <mdb-tbl-body v-for="(item, index) in this.rows" :key="index">
                  <tr>
                    <!-- <th scope="row">1</th> -->
                    <td>{{ item.subject }}</td>
                    <td>{{ item.teacher }}</td>
                    <td>{{ item.schedule }}</td>
                  </tr>
                </mdb-tbl-body>
              </mdb-tbl>
            </mdb-scrollbar>
          </b-form-group>
        </b-card>
      </center>

      </div>
      
      
    </div>
  </center>
</template>
    

<style scoped lang="scss">
@import "assets/colors.scss";

.b-card {
  margin-top: 1%;
}
.jumbotron {
  padding: 0.5%;
}

#del {
  background-color: transparent;
  color: $danger;
}

.scroll{
  overflow: scroll;
  height: 500px;
  margin-top: 20px;
}

mdb-scrollbar {
  margin-top: 20%;
  padding-top: 5%;
}
</style>

<script>
import { mdbTbl, mdbTblHead, mdbTblBody, mdbScrollbar } from "mdbvue";
export default {
  name: "TableScrollPage",
  components: {
    mdbTbl,
    mdbTblHead,
    mdbTblBody,
    mdbScrollbar
  },

  data() {
    return {
      rows: [],
      infos: {
        subject: "",
        teacher: "",
        schedule: ""
      }
    };
  },
  methods: {
    deleteItem() {
      for (let i = 0; i < this.rows.length; i++) {
        if (this.rows[i].subject === this.infos.del) {
          if (this.rows.splice(this.rows.indexOf(this.rows[i]), 1));
        }
      }
      this.infos.del = "";
    },
    addItem() {
      var object = {
        subject: this.infos.subject,
        teacher: this.infos.teacher,
        schedule: this.infos.schedule
      };
      this.rows.push(object);
      this.infos.subject = "";
      this.infos.teacher = "";
      this.infos.schedule = "";
          }
  }
};
</script>

