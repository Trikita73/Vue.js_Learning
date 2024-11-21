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

