<template>
  <div class="container"> <br>
    <h1> Vue Form Validation </h1> <br>
    <div class="form-group">
      <label for="email"> Email Address:</label>
      <input type="email" id="email" class="form-control" name="email" v-model="userData.email">
    </div>
    <div class="form-group">
      <label for="password"> Password:</label>
      <input type="password" id="password" class="form-control" name="password" v-model="userData.password">
    </div>
    <div class="form-group">
      <label for="satisfaction"> Satisfaction (10 for best , 1 for wrost)</label>
      <input type="number" min="1" max="10" id="satisfaction" class="form-control" name="satisfaction" v-model.number="userData.satisfaction">
    </div>
    <div class="form-group">
      <label for="message"> Message:</label> 
      <textarea name="message" id="message" cols="30" rows="5" class="form-control" v-model="message" placeholder="Describe your message---"></textarea>
    </div>
    <div class="form-group">
      <label for="sendSpecial">
        <input type="checkbox" id="sendSpecial" name="sendSpecial" value="sendSpecial" v-model="checkboxOptions"> Today is special day
      </label>
      <br>
    <label for="sendcupon">
        <input type="checkbox" id="sendcupon" name="sendcupon" value="sendcupon" v-model="checkboxOptions"> Give monthly Cupons
      </label>
    </div>
    <div class="form-group">
      <label for="male"> Male
        <input type="radio" name="male" id="male" value="male" v-model="radioOptions">
      </label>
      <label for="female"> Female
        <input type="radio" name="female" id="female" value="female" v-model="radioOptions">
      </label>
    </div>
    <div class="form-group">
      <label for="priority">Priority
        <select name="priority" id="priority" v-model="selectedPriority">
          <option v-for="priority in priorities" :key="priority">{{priority}}</option>
        </select>
      </label>
    </div>
    <div class="form-group">
      <button class="btn btn-primary"
        @click.prevent="submitted">submit</button>
    </div>
    <div class="card" mt-5 v-if="isSubmitted">
    <div class="card-body">
      <h3 class="card-title">Form Data</h3>
      <p>Email: <b> {{userData.email}} </b></p>
      <p>Password: <b> {{userData.password}} </b></p>
      <p>Satisfaction: <b> {{userData.satisfaction}} </b></p>
      <p>Message: <b> {{message}} </b></p>
      <p> CheckboxOptions:
        <ul>
          <li v-for="item in checkboxOptions" :key="item"> <b>{{item}}</b> </li>
        </ul>
      </p>
      <p>Gender: <b> {{radioOptions}}</b></p>
      <p>Priority: <b>{{selectedPriority}}</b></p>
    </div>
  </div>
  </div>
  
</template>

<script>


export default {
  name: 'App',
  data(){
      return {
        userData: {
          email:'',
          password:'',
          satisfaction: 10
        },
        message:'',
        checkboxOptions: [],
        radioOptions: 'male',
        selectedPriority:'High',
        priorities: ['High','Medium', 'Low'],
        isSubmitted: false
      }
    },
    methods:{
      submitted(){
        this.isSubmitted=true;
      }
    },
    
  components: {
    
  }
}
</script>

<style>

</style>
