<template>
    <div>
        <p>{{task.title}} </p>
        <div class="buttons-group">
            <input class="styled-checkbox" :id="'styled-checkbox-' + index" type="checkbox"
                   @change="done(task, index)">
            <label :for="'styled-checkbox-' + index"></label>
            <button class="action-btn delete" v-on:click="removeTask(task,index)">X</button>
        </div>
    </div>
</template>

<script>

    export default {
        props: {
            index: Number,
            task: Object,
            tasks: Array,
        },
        methods: {
            removeTask(task, index) {
                let vm = this;
                vm.$emit('remove-task', task);
            },
            done(task) {
                task.isDone = true;
            },

        },
        computed: {
            newTasks: function () {
                return this.tasks.filter(function (task) {
                    return task.isDone === false;
                })
            }
        }
    }
</script>
<style scoped>
    .heading h3 {
        font-weight: bold;
        margin-bottom: 50px;
    }

    .row-todo input {
        width: 85%;
        border-radius: 4px;
        border: 1px solid #e6e6e6;
        padding: 0 15px;
    }

    .row-todo input:focus {
        outline: none;
        box-shadow: none !important;
        border: unset !important;
    }

    .row-todo label {
        font-size: 20px;
        font-weight: bold;
        padding: 0 35px;
    }

    .todo-list-content .content h2 {
        font-size: 35px;
        text-align: left;
        font-weight: bold;
    }

    .task-item .buttons-group {
        float: right;
        display: flex;
    }

    .task-item p, .task-item div {
        display: inline-block;
    }

    .action-btn {
        width: 26px;
        height: 26px;
        border-radius: 2px;
        border: none;
        margin-left: 5px;
        color: #fff;
    }

    .action-btn.success {
        background-color: #5eb75e;
    }

    .action-btn.success img {
        display: block;
        width: 13px;
    }

    .action-btn.delete {
        background-color: #d5544d;
    }

    .styled-checkbox {
        position: absolute;
        opacity: 0;
    }

    .styled-checkbox + label {
        position: relative;
        cursor: pointer;
        padding: 0;
        width: 26px;
        height: 26px;
        border: 1px solid #5eb75e;
        border-radius: 2px;
    }

    .styled-checkbox + label:before {
        content: '';
        display: inline-block;
        width: 100%;
        height: 100%;
        background: white;
    }

    .styled-checkbox + label:before {
        background: #5eb75e;
    }

    .styled-checkbox + label:after {
        content: '';
        position: absolute;
        left: 7px;
        top: 10px;
        background: white;
        width: 2px;
        height: 2px;
        box-shadow: 2px 0 0 white,
        4px 0 0 white,
        4px -2px 0 white,
        4px -4px 0 white,
        4px -6px 0 white,
        4px -8px 0 white;
        transform: rotate(45deg);
    }
</style>