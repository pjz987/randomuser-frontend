<template>
  <div class="col s12 l4 m6">
    <div class="card horizontal grey lighten-3">
      <div class="card-image">
        <img :src="user.picture.large"/>
      </div>
      <div class="card-content">
        <h5 class="left-align bold">{{ user.name.first }} {{ user.name.last }}</h5>
        <a :href="user.email">{{ user.email }}</a>
        <div v-show="!cellPhoneWidth" class="left-align">{{ user.cell }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RandomUser',
  props: {
    user: Object,
    cellPhoneWidth: Boolean
    }
  }
</script>

<style scoped>
  .bold {
    font-weight: bold;
  }
  .card {
    box-shadow: none;
  }
</style>