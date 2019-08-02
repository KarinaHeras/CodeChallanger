<template>
  <div id="app">

    <main>
        <h2>Click the button to get Random Users</h2>
        <button id="btn" class="btn__get" v-on:click="getusers">Get users</button>

        <div v-if="loading">
          <img src="../src/assets/loader.gif"/>
          Loading.....
        </div>
          <div v-for="user in users">

          <div class="card">
            <div>
              <img v-bind:src="user.picture.medium">
              <div class="card__wapper">
                 <h3>Hi, My name is  {{ user.name.first }} {{user.name.last}}</h3>
                 <ul class="card__list">
                   <li class="card__list__item--location"><img src= "../src/assets/map-location.svg" alt="map-location">{{ user.location.city }}</li>
                   <li class="card__list__item--phone"><img src= "../src/assets/phone-call.svg" alt="phone-call">{{user.cell}} </li>
                   <li class="card__list__item--mail"><img src= "../src/assets/email.svg" alt="email">{{user.email}}</li>
                   
                 </ul>
              
              </div>              
              
            </div>
          </div>
        </div>
       
    </main>
  </div>
</template>

<script>
import axios from 'axios';
  
export default {
  name: 'app',
  data () {
    return {
      users: [],
      loading: false
    }
  }, 
  methods: {
    getusers: function () {
      this.loading = true;
      axios.get("https://randomuser.me/api/?results=3")
      .then((response)  =>  {
        this.loading = false;
        this.users = response.data.results;
       
      }, (error)  =>  {
        this.loading = false;
      })
    }
  },
}
</script>

<style>
  


</style>