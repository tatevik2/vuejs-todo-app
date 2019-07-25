<template>
    <div class="main-content">
        <div class="heading">
            <h3>To-Do list </h3>
        </div>
        <div class="row-content">
            <div class="todo-list-content row-item">
                <div class="content">
                    <div class="row-content">
                        <div class="added-task">
                            <ul class="task-list">
                                <li v-for="(task, index) in newTasks" class="task-item" v-bind:key="task.key">
                                    <Item v-on:remove-task="removeTask" :index="index" :task="task" :tasks=tasks></Item>
                                </li>
                            </ul>
                        </div>
                    </div>
                    <AddItem :tasks="tasks"></AddItem>
                </div>
            </div>
            <List :tasks="tasks"></List>
        </div>
    </div>
</template>

<script>

    import List from '../list/List.vue';
    import AddItem from '../add-item/AddItem.vue';
    import Item from '../item/Item.vue';

    export default {
        components: {
            List,
            AddItem,
            Item,
        },
        data() {
            return {
                tasks: []
            };
        },
        computed: {
            newTasks: function () {
                return this.tasks.filter(function (task) {
                    return task.isDone === false;
                })
            },
        },
        methods: {
            removeTask(task) {
                let vm = this;
                const taskIndex = vm.tasks.indexOf(task);
                vm.tasks.splice(taskIndex, 1);
            },
        }
    }
</script>
<style scoped>
    .main-content {
        padding: 0 10%;
    }

    .heading h3 {
        font-weight: bold;
        margin-bottom: 50px;
    }

    .row-content {
        width: 100%;
        display: flex;
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

    .row-item {
        width: 50%;
        padding: 0 15px;

    }

    .content {
        width: 100%;
        min-height: 500px;
        height: auto;
        padding: 20px;
        background-color: #f5f5f5;
        border: 1px solid #e6e6e6;
        border-radius: 4px;
    }

    .todo-list-content .content h2 {
        font-size: 35px;
        text-align: left;
        font-weight: bold;
    }

    .added-task {
        width: 100%;
    }

    .task-list {
        width: 100%;
        padding: 0;
    }

    .task-item {
        list-style-type: none;
        height: 50px;
        max-height: 50px;
        background-color: #fff;
        border: 1px solid #e6e6e6;
        margin-bottom: 0;
        text-align: left;
        padding: 10px 15px;
        border-radius: 4px;
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