<template>
  <div id="app">
    <main>
      <h2>Click the button to get Random Users</h2>
      <button id="btn" class="btn__get" v-on:click="getusers">Get users</button>

      <div v-if="loading">
        <img src="../src/assets/loader.gif" class="loading" />
        Loading.....
      </div>
      <div class="container">
        <div class="row justify-content-md-center">
          <div class="col-md-auto">
            <div v-for="user in users">
              <div class="card">
                <div>
                  <img v-bind:src="user.picture.large" class="post" />

                  <div class="card__wapper">
                    <h3>Mr {{ user.name.first }} {{user.name.last}}</h3>

                    <ul class="card__list">
                      <li class="card__list__item--location">
                        <img src="../src/assets/worldwide.svg" alt="map-location" />
                        {{ user.location.city }}
                      </li>
                      <li class="card__list__item--phone">
                        <img src="../src/assets/phone-call.svg" alt="phone-call" />
                        {{user.cell}}
                      </li>
                      <li class="card__list__item--email">
                        <img src="../src/assets/email.svg" alt="email" />
                        {{user.email}}
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      users: [],
      loading: false
    };
  },
  methods: {
    getusers: function() {
      this.loading = true;
      axios.get("https://randomuser.me/api/?results=1").then(
        response => {
          this.loading = false;
          this.users = response.data.results;
        },
        error => {
          this.loading = false;
        }
      );
    }
  }
};
</script>

<style>
.loading {
  width: 20px;
  height: 20px;
}
button:focus {
  outline: 0;
}
main {
  padding: 3rem;
}
h2 {
  text-align: center;
  color: rgb(83, 79, 79);
  font-family: Helvetica, sans-serif;
  font-size: 2rem;
  font-weight: bold;
}
.btn__get {
  width: 9rem;
  border-radius: 1rem;
  padding: 0.5rem;
  margin-left: 7rem;

  text-decoration: none;
  cursor: pointer;
}
h3 {
  text-transform: capitalize;
  font-size: 1.5rem;
  font-family: Helvetica, sans-serif;
  font-weight: bold;
  text-align: center;
  cursor: pointer;
  margin: 1rem;
}

.text-title {
  text-transform: capitalize;
}
.card__list__item--location {
  text-transform: capitalize;
}
.card__list__item--location img {
  width: 20px;
  height: 20px;
}
:active.card__list__item--location,
:active.card__list__item--phone,
:active.card__list__item--email {
  color: rgb(180, 240, 235);
}
.card__list__item--phone img {
  width: 20px;
  height: 20px;
}

.card__list__item--email img {
  width: 20px;
  height: 20px;
}
.card .post {
  width: 100%;
  position: relative;
}
ul li {
  list-style: none;
  padding: 10px 30px 10px 30px;
  text-align: left;
  min-width: 300px;
  max-width: 300px;
}
.card__wapper {
}
.card {
  font-family: "Roboto", Arial, sans-serif;
  position: relative;
  float: left;
  overflow: hidden;
  margin: 10px 1%;
  min-width: 230px;
  max-width: 315px;
  width: 100%;
  color: #0e0d0d;
  text-align: left;
  line-height: 1.4em;
  background-color: #e7eaeb;
  border-radius: 10px;
  -webkit-box-shadow: 10px 10px 5px 0px rgba(226, 224, 224, 0.75);
}

.card:hover {
  top: -2px;
  box-shadow: 0 4px 5px rgba(0, 0, 0, 0.2);
}

.card__list:hover {
  margin-top: 0px;
  outline: 0 solid #fff;
  border-top: 0px solid #fff;
  border-bottom: 1px solid #fff;
}
.card img {
  max-width: 100%;
  vertical-align: top;
  opacity: 0.85;
}

.card__list {
  position: relative;
  z-index: 10;
  font-family: Helvetica, sans-serif;
  font-size: rem;
  padding: 15px;
  bottom: 0px;
  transition: all 0.5s ease;
}
.card:before {
  content: "";
  position: absolute;
  top: 0px;
  left: 0px;
  width: 0px;
  height: 100%;
  background: rgba(255, 255, 255, 0.1);
  transition: all 1s ease;
}
.card:hover:before {
  width: 100%;
}
</style>