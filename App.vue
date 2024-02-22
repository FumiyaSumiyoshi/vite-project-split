<script>
//TodoOperationをインポート
import TodoOperation from './components/TodoOperation.vue'
import TodoList from './components/TodoList.vue'

export default {
  //OptionsAPIのcomponentsオプションで登録
  components: {
    TodoOperation,
    TodoList,
  },
  data() {
    return {
      //TodoOperationに移したためコメントアウト
      //newTodoText: '',
      todos: [],
    }
  },
  methods: {
    //新しいTodoを取得するためのinputタグをTodoOperationに移行したためメソッドの修正
    addTodo(newTodoText) {
      if (!newTodoText) return alert('文字を入力してください')
      this.todos.push({
        isDone: false,
        text: newTodoText,
      })
      //以下の初期化処理は
      //this.newTodoText = ''
    },
    clearDoneTodos() {
      //完了チェックがついていないtodoを要素とする新たな配列をtodosにセットする
      this.todos = this.todos.filter((todo) => !todo.isDone)
    },
  },
}
</script>

<template>
  <h1>My ToDo App</h1>
  <!-- clearDoneTodosメソッドにdelete-doneを紐づけることで、 -->
  <!-- TodoOperationに定義してある削除ボタンが謳歌された時に発火する -->
  <br>
  <TodoOperation @add-todo="addTodo" @delete-done="clearDoneTodos"/>
  <p v-if="todos.length === 0">ToDoがまだありません！</p>
  <TodoList v-else :todos="todos" />
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>
