<template>
  <div class="div" id="app">
    {{ user.username }} - {{ fullName }}
    <strong> follower: </strong> {{ follower }}
    <button @click="followUser">
      Follow
    </button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      follower: 0,
      user: {
        id: 1,
        username: '@Fr_Azhar27',
        firtname: 'Fajar',
        lastname: 'Ramadhan',
        email: 'fajarramadhan220@gmail.com',
        isAdmin: true,
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firtname} ${this.user.lastname}`
    }
  },
  methods: {
    followUser() {
      this.follower++;
    }
  },
  mounted() {
    this.followUser()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>
