<template>
  <div class="container">
    <form action="">
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h1>File a Complaint</h1>
          <hr>
          <div class="form-group">
            <label for="email">Mail</label>
            <input
              type="text"
              id="email"
              class="form-control"
              :v-model.lazy="userData.email">
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              type="password"
              id="password"
              class="form-control"
              :v-model.lazy="userData.password">
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input
              type="number"
              id="age"
              class="form-control"
              :v-model.lazy="userData.age">
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <label for="message">Message</label>
          <!--Interpolation between <textarea>{{ test }}</textarea> doesn't work-->
          <textarea
            id="message"
            rows="5"
            class="form-control"
            v-model="message"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <div class="form-group">
            <label for="sendmail">
            <input
              type="checkbox"
              id="sendmail"
              value="Send Mail"
              v-model="sendMail"> Send Mail
            </label>
            <label for="sendInfomail">
              <input
                type="checkbox"
                id="sendInfomail"
                value="SendInfoMail"
                v-model="sendMail">Send Info Mail
            </label>
            <!--Also show for single checkbox with true/false-->
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <label for="male">
            <input
              type="radio"
              id="male"
              value="Male"
              v-model="gender">Male
          </label>
          <label for="female">
            <input
              type="radio"
              id="female"
              value="Female"
              v-model="gender">Female
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <label for="priority">Priority</label>
          <select
            id="priority"
            class="form-control"
            :v-model="selectedPriority">
            <option
              value=""
              v-for="priority in priorities">
              {{ priority }}
            </option>
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <app-switch v-model="dataSwitch"></app-switch>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <hr>
          <button
            class="btn btn-primary"
            @click.prevent="submitted">Submit!</button>
          <hr>
        </div>
      </div>
      <div class="row" v-if="isSubmitted">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <div class="panel panel-default">
            <div class="panel-heading">
              <h4>Your data</h4>
              <div class="panel-body">
                <p>Mail: {{ userData.email }}</p>
                <p>Password: {{ userData.password }}</p>
                <p>Age: {{ userData.age }}</p>
                <p style="white-space: pre">Message: {{ message }}</p>
                <p><strong>Send Mail?</strong></p>
                <ul>
                  <li v-for="item in sendMail">{{ item }}</li>
                </ul>
                <p>Gender: {{ gender }}</p>
                <p>Priority: {{ selectedPriority }}</p>
                <p>Switched: {{ dataSwitch }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  import Switch from './Switch.vue'

  export default {
    data(){
      return {
        userData: {
          email: '',
          password: '',
          age: 20
        },
        message: 'A new Text',
        sendMail: [],
        gender: 'Male',
        selectedPriority: 'High',
        priorities: ['High', 'Medium', 'Low'],
        dataSwitch: true,
        isSubmitted: false
      }
    },
    methods: {
      submitted(){
        this.isSubmitted = true;
      }
    },
    components: {
      appSwitch: Switch
    }
  }
</script>

<style>
  .container {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
