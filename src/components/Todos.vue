<template>
    <section>
        <TodoItem v-bind:key="todo.id"
                  v-for="todo in todos"
                  v-bind:todo="todo"
                  v-on:del-todo="$emit('del-todo', todo.id)"/>
    </section>
</template>

<script>
import TodoItem from './TodoItem';

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>

</style>