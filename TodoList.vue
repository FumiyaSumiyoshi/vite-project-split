<script>
export default {
    //Appから渡されるtodosを定義
    props: {
        todos: Array,
    },
}
</script>

<template>
  <ul>
    <!-- Appから受け取ったtodosを回してリストで表示 -->
    <li v-for="(todo, key) in todos" :key="key">
      <input type="checkbox" v-model="todo.isDone" /><span
        :class="{ 'todo-done': todo.isDone }"
        >{{ todo.text }}</span
      >
    </li>
  </ul>
</template>
