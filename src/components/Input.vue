<template>
    <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Введите число"><br>
    <button className="button_current" @click="convert()">Конвертировать</button>
    <button className="button_favourite" @click="favourite()">В избранное</button>
  </template>
  
  <script>
  export default {
    props: {
      changeAmount: {
        type: Function,
        required: true
      },
      convert: {
        type: Function,
        required: true
      },
      favourite: {
        type: Function,
        required: true
      }
    }
  }
  </script>

  <style scoped>
  input {
    outline: none;
    width: 500px;
    position: relative;
    top: -20px;
    font-size: 1.2em;
    border-radius: 3px;
    border: 4px solid #1a032d;
    padding: 10px 15px;
    background: #fafafa;
    color: #333
  }
  .button_current {
    top: -20px;
    padding: 15px 20px;
    color: #fff;
    text-transform: uppercase;
    cursor: pointer;
    background: #1a032d;
    border-radius: 3px;
    border: 3px solid #000;
    transition: transform 500ms ease;
  }
  .button_current:hover, li.active {
    background: #24043e;
    cursor: pointer;
  }
  .button_current:hover {
    transform: scale(1.1);
  }
  .button_favourite {
    margin-left: 20px;
    top: -20px;
    padding: 15px 20px;
    color: #fff;
    text-transform: uppercase;
    cursor: pointer;
    background: #1a032d;
    border-radius: 3px;
    border: 3px solid #000;
    transition: transform 500ms ease;
  }
  .button_favourite:hover, li.active {
    background: #24043e;
    cursor: pointer;
  }
  .button_favourite:hover {
    transform: scale(1.1);
  }
  </style>
  