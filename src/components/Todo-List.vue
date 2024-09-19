<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                Vue Todo List
            </div>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6">
                <NewTodo @add-todo="addTodo"/>
            </div>
            </div>

        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <TodoItem v-for="(todo, id) in todos" :key="id" :todo="todo" :todoData="todo.text" :completed="todo.done" 
                    @on-delete="deleteTodo(todo)" @edit-todo="editTodo(todo, $event)" @toggle-done="toggleDone(todo)"
                    />
                </ul> 
            </div>
            </div>
    </div>
</template>

<script>
import TodoItem from './Todo.vue';
import NewTodo from './NewTodo.vue';

export default {
    name: 'TodoList',
    components: {
        TodoItem,
        NewTodo
    },
    data() {
        return {
            todos: [
                { id: 1, text: 'Learn Vue', done: true },
                { id: 2, text: 'Learn Vuex', done: false },
                { id: 3, text: 'Learn Vue Router', done: false }
            ]
        }
    },

    methods: {
        toggleDone(todo) {
            todo.done = !todo.done;
        },
        addTodo(newTodo) {
            this.todos.push({
                id: this.todos.length + 1,
                text: newTodo,
                done: false
            });
        },
        editTodo(todo , newText) {
            todo.text = newText;
        },
        deleteTodo (todo) {
            this.todos = this.todos.filter(t => t.id !== todo.id);
        }
    }



}
</script>

<style>
</style>