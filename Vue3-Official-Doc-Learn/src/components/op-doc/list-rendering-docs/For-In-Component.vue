<script>
import TodoItem from './TodoItem.vue'

export default {
    data() {
        return {
            newTodoText: '',
            todos: [
                { id: 1, title: 'Do the dishes' },
                { id: 2, title: 'Take out the trash' },
                { id: 3, title: 'Mow the lawn' }
            ],
            nextTodoId: 4
        }
    },
    components: { TodoItem },
    methods: {
        addNewTodo() {
            this.todos.push({
                id: this.nextTodoId++,
                title: this.newTodoText
            })
            this.newTodoText = ''
        }
    }
}
</script>
<template>
    <form v-on:submit.prevent="addNewTodo">
        <label for="new-todo">Add a todo</label>
        <input v-model="newTodoText" id="new-todo" placeholder="E.g. Feed the cat" />
        <button>Add</button>
    </form>
    <ul>
        <todo-item v-for="(todo, index) in todos" :key="todo.id" :title="todo.title" :id="todo.id"
            @remove="todos.splice(index, 1)"></todo-item>
    </ul>
</template>