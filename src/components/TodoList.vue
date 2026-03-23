<script setup>
import { useTodoListStore } from '@/stores/todoList';
import { storeToRefs } from 'pinia';
import { compile } from 'vue';

const store = useTodoListStore();

const {todoList} = storeToRefs(store);

const { toggleCompleted, deleteTodo } = store

</script>

<template>
    <div>
        <div v-for="todo in todoList" :key="todoList.id" class="item">
            <div class="content">
                <span :class="{completed: todo.completed}">{{ todo.item }}</span>
                <span @click.stop="toggleCompleted(todo.id)" class="tick">&#10004;</span>
                <span @click="deleteTodo(todo.id)" class="x">&#10060;</span>
            </div>
           
        </div>
    </div>
</template>

<style scoped>
.completed {
    text-decoration: line-through;
}
.x {
    margin: 1%;
}
.tick {
    margin: 1%;
}
</style>