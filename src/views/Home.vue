<template>
  <div class="home">
    <!--<img alt="Vue logo" src="../assets/logo.png" />-->
    <v-container>
      <v-row>
        <v-col cols="10">
          <v-text-field name="name" label="Task" id="id" v-model="taskTextField"></v-text-field>
        </v-col>
        <v-col cols="2">
        <v-btn class="block" color="success" @click="addTask">ADD</v-btn>
        </v-col>
      </v-row>
      <v-card>
        <v-card-title primary-title>
          <v-container>
            <v-row class="d-flex flex-row align-center pa-0" v-for="(items,index) in todos" :key="index">
              <v-col cols="12" class="d-flex flex-row align-center">
                <v-checkbox v-model="value" value="value" class="mr-1"></v-checkbox>
                <span>{{items.title}}</span>
                <v-spacer></v-spacer>
                <v-btn color="error">x</v-btn>
              </v-col>
              <v-col cols="12">
                <v-divider></v-divider>
              </v-col>
            </v-row>
          </v-container>
        </v-card-title>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios"
export default {
  name: "Home",
  components: {
    //HelloWorld
  },
  async mounted(){
      var x=0;
      console.log("mounted="+x);
      let result = await axios.get("https://jsonplaceholder.typicode.com/todos")
      this.todos=result.data
  },
  methods: {
    async addTask(){
      //let result = await axios.post("https://jsonplaceholder.typicode.com/todos",this.taskTextField)
      //this.todos.push(resut.data);
      /*this.todos.push({
        id: Math.random,
        title:this.taskTextField,
        completed: false
      })*/
      this.taskTextField=""
    }
  },
  data() {
    return {
      taskTextField:"",
      todos_mockup: [
        { id: 1, title: "Task 1", completed: false },
        { id: 2, title: "Task 2", completed: true },
        { id: 3, title: "Task 3", completed: true }
      ],
      todos:[

      ]
    };
  }
};
</script>
