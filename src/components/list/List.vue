<template>
    <div class="col-6">
        <table id="tasks">
            <tr>
                <th>List</th>
            </tr>
            <tr v-for="task in doneTasks" v-bind:key="task.key">
                <td>{{task.title}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        props: {
            tasks: Array
        },
        computed: {
            doneTasks: function () {
                return this.tasks.filter(function (task) {
                    return task.isDone === true;
                })
            }
        }
    }
</script>

<style scoped>
    /*table*/
    #tasks {
        font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
        border-collapse: collapse;
        width: 100%;
    }

    #tasks td, #tasks th {
        border: 1px solid #ddd;
        padding: 8px;
    }

    #tasks tr:nth-child(even) {
        background-color: #f2f2f2;
    }

    #tasks tr {
        cursor: pointer;
    }

    #tasks tr:hover {
        background-color: #ddd;
    }

    #tasks th {
        padding-top: 12px;
        padding-bottom: 12px;
        background-color: #f5f5f5;
        text-align: center;
        color: black;
        font-size: 17px;
    }
</style>