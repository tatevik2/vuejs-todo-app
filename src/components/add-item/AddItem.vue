<template>
    <div class="add-task-content">
        <div class="row-content row-todo">
            <label for="taskName">Task</label>
            <input type="text" id="taskName" class="task-name" v-model="newTask.title">
        </div>
        <div class="btn-content">
            <button class="add-task-btn" type="button" v-on:click="add()">Save Item</button>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            tasks: Array
        },
        data() {
            return {
                newTask: {
                    title: '',
                    isDone: false
                }
            };
        },
        methods: {
            add() {
                let vm = this;
                if (vm.newTask.title.length > 0) {
                    vm.tasks.push(
                        vm.newTask
                    );
                    vm.newTask = {
                        title: '',
                        isDone: false
                    };
                }
                return;
            }
        }
    }
</script>
<style scoped>
    .heading h3 {
        font-weight: bold;
        margin-bottom: 50px;
    }

    .row-content {
        width: 100%;
        display: flex;
    }

    .row-todo {
        justify-content: flex-end;
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

    .btn-content {
        text-align: right;
    }

    .add-task-btn {
        height: 40px;
        padding: 0 15px;
        background: #3579b6;
        border: none;
        border-radius: 4px;
        color: #fff;
        margin-top: 20px;
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

    .action-btn.success img {
        display: block;
        width: 13px;
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