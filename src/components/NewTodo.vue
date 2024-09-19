<template>
    <div>
<form action="" class="col-12 col-lf-6">
    <div class="form-group">
        <input type="text" class="form-control" v-model="newTodo" placeholder="Add new todo">
    </div>
    <button class="btn btn-primary" @click.prevent="addTodo">Add Todo</button>
</form>
    </div>
</template>

<script>
export default {
    name: 'NewTodo',
    data() {
        return {
            newTodo: ''
        }
    },
    methods: {
        addTodo() {
            this.$emit('add-todo', this.newTodo);
            this.newTodo = '';
        }
    }
}
</script>

<style scoped>

</style>