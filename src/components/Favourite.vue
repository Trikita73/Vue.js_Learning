<template>
    <h2>Варианты в избранном</h2>
    <div className="favourite_items" v-for="(el, index) in favs" :key="index">
        <span> {{ el.from }}</span>
        <span> {{ el.to }}</span>
    </div>  
</template>
  
<script>
export default {
    props: {
        favs: {
            type: Array,
            Required: true
        }
    }
} 
</script>
 
  <style scoped>
    h2 {
        color: #24043e;
    }
    .favourite_items {
        display: flex;
        justify-content: space-around;
        width: 500px;
        margin: 10px auto;
        transition: all 500ms ease;
    }
    .favourite_items span {
        padding: 10px 15px;
        background: #8c00ff;
        color: #fff;
    }
    .favourite_items:hover {
        opacity: 0.7;
        transform: scale(1.1);
        cursor: pointer;
    }
  </style>
  