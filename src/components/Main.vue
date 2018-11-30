<template>

    <v-layout column>
        <v-flex xs12 sm6>
            <v-card>
                <v-toolbar color="cyan" dark>
                    <v-toolbar-title>TODO List</v-toolbar-title>
                    </v-toolbar>
                    <v-list two-line>
                    <v-list-tile >
                        <v-list-tile-content class="textContent">
                            <v-text-field color="cyan" @keyup.enter="addNewTask(inputText)" light placeholder="Add new Task" class="inputText" v-model="inputText"></v-text-field>
                        </v-list-tile-content>
                        <v-list-tile-action>
                            <v-btn round small fab outline @click="addNewTask(inputText)" color="cyan lighthen-2">Add</v-btn>
                        </v-list-tile-action>
                    </v-list-tile>
                    <template v-for="task in taskList" :v-model="taskList">
                    <v-divider :key="task"></v-divider>
                    <v-list-tile :key="task">
                        <v-list-tile-content class="textContent">{{task.name}}</v-list-tile-content>
                        <v-list-tile-action>
                            <v-btn round outline small fab @click="doTask(task)" color="cyan darken-4">Done</v-btn>
                        </v-list-tile-action>
                        &nbsp;
                        <v-list-tile-action>
                            <v-btn round small fab outline @click="deleteTask(task)" color="deep-orange accent-3">Del</v-btn>
                        </v-list-tile-action>
                    </v-list-tile>
                    </template>
                    <v-divider></v-divider>
                    </v-list>
            </v-card>
            <v-card>
                <v-toolbar color="lime">
                    <v-toolbar-title>Done Tasks</v-toolbar-title>
                </v-toolbar>
                <v-list two-line>
                <template v-for="doneTask in doneList" :v-model="doneList">
                    <v-divider :key="doneTask"></v-divider>         
                    <v-list-tile :key="doneTask" color="grey lighten-1">
                        <v-list-tile-content class="crossedText">{{doneTask.name}}</v-list-tile-content>
                        <v-list-tile-action>
                            <v-btn round outline small fab @click="unDoneTask(doneTask)" color="cyan" light>Undo</v-btn>
                        </v-list-tile-action>
                        &nbsp;
                        <v-list-tile-action>
                            <v-btn round outline small fab @click="deleteDoneTask(doneTask)" color="deep-orange accent-3">Del</v-btn>
                        </v-list-tile-action>
                    </v-list-tile>
                    
                </template>
                </v-list>
            </v-card>
        </v-flex>
    </v-layout>
    
</template>

<script>
export default {
    data() {
        return{
            inputText: '',
            taskList: [
                {name: 'Task One'},
                {name: 'Task Two'}
            ],
            doneList: [
                {name: 'Done Task'}
            ]

        }
    },

    methods:{
        addNewTask(value) {
            this.taskList.push({name: value});
            this.inputText='';
        },
        doTask(task) {
            this.taskList.splice(this.taskList.indexOf(task.name),1);
            this.doneList.push(task);
        },
        deleteTask(task) {
            this.taskList.splice(this.taskList.indexOf(task.name),1);
        },
        unDoneTask(doneTask) {
            this.doneList.splice(this.doneList.indexOf(doneTask.name),1);
            this.taskList.push(doneTask);
        },
        deleteDoneTask(doneTask) {
            this.doneList.splice(this.doneList.indexOf(doneTask.name),1);
        }
    }
}
</script>

<style lang="scss">
    ul.taskList{
        list-style-type: none;
        padding: 10px;
    }

    .inputText{
        width: 75%;
        padding: 2px;
    }

    .crossedText{
        text-decoration: line-through;
    }

</style>

