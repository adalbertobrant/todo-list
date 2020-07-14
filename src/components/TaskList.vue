
<template>
    <ul class="todo-list">
 
        <li v-for="(todo, index) in sortedTasks" class="todo" :key="index">
            <div clas="view">
                <input class="toggle" @click="completeTask(todo)" type="checkbox">
                <label v-bind:class="{ 'todo-completed': todo.completed }" >{{ todo.title }}</label>
            </div>
        </li>
    </ul>
</template>

<script>
export default {
    props: ['todoList'],
    computed: {
        sortedTasks: function () {
        let sorted = this.todoList.slice()
        return sorted.sort(function (a, b) {
            if (a.title < b.title) return -1
            if (a.title > b.title) return 1
            return 0
        })
        }
  }
}
</script>