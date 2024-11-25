// Переменные и обработка данных

<!--

// css
<style scoped>
h3 {
  font-weight: lighter;
}

p {
  color: rgb(94, 42, 42);
}
</style>

// Java Script
<script>
export default {
  data() {
    return {
      info: 'Title!',
      someInfo: 'Anons of message',
      someClick: 'text of click'
    }
  },
  methods: {
    userData () {
      this.info = 'Some new'
    },
    userClick (text = 'New text') {
      this.someClick = text
    }
  }
}
</script>

// HTML
<template>
  <h3>{{ info }}</h3>
  <p>{{ someInfo }}</p>
  <p>{{ someClick }}</p>

  <button type="button" v-on:click="userData ()">Отправить</button>
  <button type="button" @mouseenter="this.someInfo = 'something interesting'">Наведи</button>
  <button type="button" v-on:click="userClick ('New text')">Кликни2</button>
</template>

-->

// работа с пользователями

<!--

// css
<style scoped>

</style>

// Java Script
<script>
export default {
  components: { User },
  data() {
    return {
      users: [],
      error: '',
      userName: '',
      userPass: '',
      userEmail: ''
    }
  },
  methods: {
    /*
    insertData(val) {
      this.userName = val
    }
    */
    sendData() {
      if(this.userName == '') {
        this.error = 'Вы не ввели имя!';
        return;
      } else if (this.userPass == '') {
        this.error = 'Вы не ввели пароль!';
        return;
      } else if (this.userEmail == '') {
        this.error = 'Вы не ввели email!';
        retun;
      }

      this.error = '';

      this.users.push({
        name: this.userName,
        pass: this.userPass,
        email: this.userEmail
      })
    }
  }
}
</script>

// HTML
<template>
  //<input type="text" @input="insertData($event.target.value)" placeholder="Имя">
  <input type="text" v-model="userName" placeholder="Имя">
  <input type="password" v-model="userPass" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="Email">
  /*
  <p> {{ userName }}</p>
  <p> {{ userPass }}</p>
  <p> {{ userEmail }}</p>
  */
  <p className="error">{{ error }}</p>
  <button @click="sendData()">Отправить</button>
  //<p>{{ users }}</p>

  <div v-if="users.length == 0">
    You don't have users
  </div>
  <div v-else-if="users.length == 1">
    You have 1 element
  </div>
  <div v-else>
    You have more than 1 element
  </div>

  <div v-for="(el, index) in users" :key="index">
    <h3>{{ el.name }}</h3>
    <p>{{ el.email }} - <b>{{ el.pass }}</b></p>
  </div>
</template>

-->


// компоненты

// css
<style scoped>
input {
  display: block;
  margin-bottom: 10px;
  border-radius: 3px;
  border: 1px solid silver;
  outline: none;
  padding: 10px 15px;
  background: #fafafa;
  color: #333;
}
button {
  border: 0;
  border-radius: 5px;
  outline: none;
  padding: 10px 15px;
  background: #6cd670;
  color: #167f3d;
  font-weight: bold;
  cursor: pointer;
  transition: transform 500ms ease;
}
button:hover {
  transform: translateY(-5px);
}
.user {
  width: 500px;
  margin-top: 20px;
  border: 1px solid silver;
  background: #e3e3e3;
  color: #222;
  padding: 20px;
  border-radius: 5px;
}
</style>

// Java Script
<script>
import User from './components/User.vue'

export default {
  components: { User },
  data() {
    return {
      users: [],
      error: '',
      userName: '',
      userPass: '',
      userEmail: ''
    }
  },
  methods: {
    sendData() {
      if(this.userName == '') {
        this.error = 'Вы не ввели имя!';
        return;
      } else if (this.userPass == '') {
        this.error = 'Вы не ввели пароль!';
        return;
      } else if (this.userEmail == '') {
        this.error = 'Вы не ввели email!';
        retun;
      }

      this.error = '';

      this.users.push({
        name: this.userName,
        pass: this.userPass,
        email: this.userEmail
      })
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    }
  }
}
</script>

// HTML
<template>
  <input type="text" v-model="userName" placeholder="Имя">
  <input type="password" v-model="userPass" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="Email">

  <p className="error">{{ error }}</p>
  <button @click="sendData()">Отправить</button>

  <div v-if="users.length == 0">
    You don't have users
  </div>
  <div v-else-if="users.length == 1">
    You have 1 element
  </div>
  <div v-else>
    You have more than 1 element
  </div>

  <User v-for="(el, index) in users" :key="index" :user="el" :index='index' :deleteUser="deleteUser" />
</template>