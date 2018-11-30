<template>

    <v-layout row>
        <v-flex sm12 sm6>
            <v-card>
                <v-toolbar color="cyan" dark>
                    <v-toolbar-title>To do List</v-toolbar-title>
                    </v-toolbar>
                    <v-list>
                    <v-list-tile >
                        <v-list-tile-content>
                            <v-text-field color="cyan" light placeholder="Add new Task" class="inputText" v-model="inputText"></v-text-field>
                        </v-list-tile-content>
                        <v-list-tile-action>
                            <v-btn @click="addNewTask(inputText)" color="cyan lighthen-2">Add</v-btn>
                        </v-list-tile-action>
                    </v-list-tile>
                    <template v-for="task in taskList" :v-model="taskList">
                    <v-divider :key="task"></v-divider>
                    <v-list-tile :key="task">
                        <v-list-tile-content>{{task.name}}</v-list-tile-content>
                        <v-list-tile-action>
                            <v-btn @click="deleteTask(task)" color="cyan darken-4">Done</v-btn>
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
            ]
        }
    },

    methods:{
        addNewTask(value) {
            this.taskList.push({name: value});
            this.inputText='';
        },
        deleteTask(task) {
            this.taskList.splice(this.taskList.indexOf(task.name),1);
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
        width: 80%;
        padding: 2px;
    }
</style>

