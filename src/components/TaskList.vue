<template>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span :class="{done: task.done}" @click="task.done = !task.done">{{task.title}}</span>
      <span class="delete" @click="$emit('delete', index)"></span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TaskList',
  props: {
    tasks: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
    list-style: none;
    padding: 0;
    margin: 0 0 40px;
}

ul li {
    margin: 5px 0;
    background: #fdfdfd;
    border: 1px solid #eee;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

span.done {
    text-decoration: line-through;
}

span {
    display: block;
    width: 100%;
    height: 100%;
    padding: 20px;
}

span.delete {
    max-width: 40px;
    height: 40px;
    display: inline-block;
    border: 2px solid #000;
    position: relative;
    padding: 0;
    margin-right: 20px;
}

span.delete:before, span.delete:after {
    content: '';
    width: 20px;
    height: 2px;
    background: #000;
    display: block;
    position: absolute;
    top: 18px;
    left: 10px;
}

span.delete:before {
    transform: rotate(45deg);
}

span.delete:after {
    transform: rotate(-45deg);
}
</style>
