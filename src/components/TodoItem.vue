<template>
    <article class="todo-item" v-bind:class="{'is-complete':todo.completed, 'is-deleted': deleted}" v-on:click="markComplete">
        <input type="checkbox" v-model="todo.completed">
        {{todo.title}}
        <button v-on:click="isDeleted" class="del">x</button>
    </article>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    data(){
        return {
            deleted: false
        }
    },
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;

            if (this.deleted)
                this.todo.completed = true;
        },
        isDeleted() {
            this.deleted = true;
            this.$emit('del-todo', this.todo.id);
        }
    },

}
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 1rem;
        border-bottom: 1px #ccc dotted;
        cursor: pointer;
        overflow: hidden;
        max-height: initial;

        display: flex;
        justify-content: space-between;
        transition: all 0.25s ease;
    }

    .todo-item:hover {

    }

    .is-complete {
        text-decoration: line-through;
        opacity: 0.25;

    }

    .is-deleted {
        /*opacity: 0;*/

        padding: 0;
        max-height: 0;
    }

    .del {
        height: 2rem;
        width: 2rem;
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        /*float: right;*/
    }
</style>