<template>
  <v-container>
    <v-layout row>
      <v-flex sm12 md12>
        <v-card>
          <!-- <v-toolbar color="primary" dark="flat">
            <v-toolbar-title>Realtime Face Recognition</v-toolbar-title>
          </v-toolbar> -->
          <div style="background: url(/check-in.png)no-repeat center fixed;
          background-size: 100% 80%;height:250px;width:100%;
          display:flex;align-items:center;justify-content:center">
          <v-btn color="primary" nuxt to="/users">
            Register
          </v-btn>
          </div>
        </v-card>
      </v-flex>
      <v-flex md12 sm12 xs12>
        <div class="d-flex justify-center mt-5">
          <p class="">Step-by-step</p>
        </div>
      </v-flex>
<v-flex md3 sm6>
        <v-card class="ma-2">
          <!-- <v-card-title>Register</v-card-title> -->
          <v-img src="/register.png" />
          <v-card-subtitle>Step I - Register Name</v-card-subtitle>
      </v-card>
      </v-flex>
      <v-flex md3 sm6>
        <v-card class="ma-2">
          <!-- <v-card-title>Take Photos</v-card-title> -->
          <v-img src="/upload.jpg" />
          <v-card-subtitle>Step II - File Upload or Camera</v-card-subtitle>
      </v-card>
      </v-flex>
      <v-flex md3 sm6>
        <v-card class="ma-2">
          <!-- <v-card-title>Train</v-card-title> -->
          <v-img src="/model.jpg" />
          <v-card-subtitle>Step III - Train model</v-card-subtitle>
      </v-card>
      </v-flex>
      <v-flex md3 sm6>
        <v-card class="ma-2">
          <!-- <v-card-title>Recognize</v-card-title> -->
          <v-img src="/facialrec.jpg" />
          <v-card-subtitle>Step IV - Recognize Face</v-card-subtitle>
      </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {}
</script>
