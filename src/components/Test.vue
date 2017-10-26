<template>
  <div class="test">
    <h1>{{title}}</h1>
    <p>{{user.firstName}}</p>
    <p v-text="user.lastName"></p>
    <!-- v-if -->
    <p v-if="showName">{{user.firstName}}</p>
    <!-- v-else -->
    <p v-else>Nobody</p>
    <!-- v-for -->
    <ul>
      <li v-for="item in items">{{item.title}}</li>
    </ul>
    <!-- v-on -->
    <button type="button" name="button" v-on:click="greet('hello world!!!')">hello</button>
    <!-- computed 计算属性 -->
    <hr>
    <label for="firstName">firstName:</label>
    <input type="text" name="firstName" value="" v-model="user.firstName">
    <br>
    <label for="lastName">lastName:</label>
    <input type="text" name="lastName" value="" v-model="user.lastName">
    <br>
    <h1>{{fullName}}</h1>
    <!-- prop -->
    <p>{{msg}}</p>
  </div>
</template>

<script>
  export default {
    name: "test",
    props: {
      msg: {
        type: String,
        default: "default value"
      }
    },
    data(){
      return {
        title: "Hello Vue.js!",
        user: {
          firstName:"hemiah",
          lastName:"wu"
        },
        showName: false,
        items: [
          {title: 'item 1'},
          {title: 'item 1'},
          {title: 'item 1'}
        ]
      }
    },
    methods: {
      greet: function (greeting) {
        alert(greeting)
      }
    },
    computed: {
      fullName: function () {
        return this.user.firstName+" "+this.user.lastName
      }
    }
  }
</script>

<style scoped>

</style>
