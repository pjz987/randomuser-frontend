<template>
  <div class="container">
    <h1 class="bold">people</h1>
    <form class="row">
      <input class="col l4 s12" placeholder="name search">
      <button class="col l2 s12 btn black" type="submit">search</button>
    </form>
    <div v-if="randomUsers.length" class="row">
      <RandomUser
        v-for="(user, i) in randomUsers"
        :key="i"
        :user="user"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import RandomUser from './components/RandomUser.vue'

export default {
  name: 'App',
  components: {
    RandomUser
  },
  data: function() {
    return {
      randomUsers: []
    }
  },
  created: function() {
    axios({
      method: 'get',
      url: 'https://randomuser.me/api/?results=12'
    }).then(res => {
      console.log(res.data)
      this.randomUsers = res.data.results
    }).catch(err => console.log(err.message))
  }
}
</script>

<style scoped>
  input {
    border: 2px solid black;
  }
  ::placeholder {
    color: black
  }
  button {
    height: 100%
  }
  .bold {
    font-weight: bold;
  }
</style>