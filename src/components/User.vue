<template>
  <div class="user">
    <h1>Users</h1>
    <!-- 添加用户信息 -->
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter name">
      <input type="text" v-model="newUser.email" placeholder="Enter email">
      <input type="submit" value="Submit">
    </form>
    <!-- 展示用户信息 -->
    <ul>
      <li v-for="user in users">
        <input type="checkbox" v-model="user.contacted">
        <span v-bind:class="{contacted: user.contacted}">
          {{user.name}} : {{user.email}}
          <button v-on:click="deleteUser(user)">X</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "user",
    data(){
      return {
        newUser:{
          name: '',
          email: ''
        },
        users:[
          {
            name: 'aa',
            email: 'aa@gmail.com',
            contacted: false
          },
          {
            name: 'bb',
            email: 'bb@gmail.com',
            contacted: false
          },
          {
            name: 'cc',
            email: 'cc@gmail.com',
            contacted: false
          }
        ]
      }
    },
    methods: {
      addUser: function (e) {
        // console.log("hello")
        this.users.push({
          name: this.newUser.name,
          email: this.newUser.email
        })
        e.preventDefault()
      },
      deleteUser: function (user) {
        this.users.splice(this.users.indexOf(user), 1)
      }
    },
    created: function () {
      // console.log("helloworld");
      this.$http.get('http://jsonplaceholder.typicode.com/users').then(function (rsp) {
        this.users = rsp.data
      })
    }
  }
</script>

<style scoped>
  .contacted {
    text-decoration: line-through;
  }
</style>
