<script>
import MyButton from './basics/MyButton.vue'

export default {
  emits: ['delete-done', 'add-todo'],
  components: {
      MyButton,
  },
  data() {
    return {
      newTodoText: '',
    }
  },
  //タスクの追加は押すたびに1つのデータを追加するため、add-todoはメソッドから発火させる。
  methods: {
    todoAdd() {
      //Vueのインスタンスに紐づく機能を使う時は「this.」を付ける必要がある
      this.$emit('add-todo', this.newTodoText)
      this.newTodoText = ''
    },
  },
}
</script>

<template>
  <input type="text" v-model="newTodoText" />
  <br>
  <MyButton @click="todoAdd">追加 <img src="../assets/icon-plus.svg" height="10" /></MyButton>
  <!-- $emit:指定した名前のイベントを任意の引数とともに発火させる。 -->
  <MyButton @click="$emit('delete-done')">完了済みを削除する</MyButton>
</template>