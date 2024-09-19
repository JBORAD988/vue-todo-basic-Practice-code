<template>
    <li class="d-flex align-items-center list-group-item">
         <input type="checkbox" :checked="completed" @change="$emit('toggle-done', !completed)">
         <span :class="{completed: completed}" v-if="!isEditing">{{ todoData }}</span>
         <input type="text" v-model="editText" v-if="isEditing" @keyup.enter="EndEditing()">
         <button @click="StartEditing">Edit</button>
         <button @click="$emit('on-delete')">Delete</button>
     </li>
 </template>
 
 <script>
 export default {
     name: 'TodoItem',
     props: {
         todoData: {
             type: String,
             required: true
         },
         completed: {
             type: Boolean,
             required: true
         }
     },
     data() {
         return {
             isEditing: false,
             editText: this.todoData
         }
     },
     methods: {
         StartEditing() {
             this.isEditing = !this.isEditing;
             if (!this.isEditing) {
                 this.editText = this.todoData; // Reset the text if editing is canceled
             }
         },
         EndEditing() {
             this.isEditing = false;
             this.$emit('edit-todo', this.editText);
         }
     }
 }
 </script>
 
 <style scoped>
 .completed {
     text-decoration: line-through;
 }
 </style>
 