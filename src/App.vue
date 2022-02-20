<template>
  <div class="container">
    <div class="form">
      <h1>{{ title }}</h1>
      <input type="text" v-model.trim="item" v-on:keyup.enter="AddTask" class="input"/>
      <button @click="AddTask">Nova Tarefa</button>
    </div>
    <Tasks :tasks="tasks">
	</Tasks>
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
export default {
  name: "App",
  components: {
    Tasks,
  },
  data() {
    return {
      title: "Tarefas",
      item: "",
      tasks: [
        { id: 1, task: "Comer coisas saudáveis", isCompleted: false },
        { id: 2, task: "Estudar mais", isCompleted: false },
        { id: 3, task: "Fazer café", isCompleted: false },
      ],
    };
  },
  methods: {
    AddTask() {
      console.log(this.item);
      this.tasks.push({
        id: this.GetLastId(),
        task: this.item,
        isCompleted: false,
      });
      this.item = ''
    },
    GetLastId() {
      if(this.tasks.length > 0){
        let task = this.tasks[this.tasks.length - 1];
        return task.id + 1;
      }
      else
        return 1
    },
  },
};
</script>

<style>
h1{
  font-weight: 820;
  margin-bottom: 40px;
}
body{
  background-color: #333333;
}
#app {
  font-family: 'Times New Roman', Times, serif, Helvetica, Arial, sans-serif;
  text-align: center;
  color: rgb(255, 255, 255);
  padding-top: 30px;
  justify-content: center;
}
.container{
  justify-content: center;
}
.form {
  margin-bottom: 3em;
}
.input{
  margin-right: 0.2em;
  margin-bottom: 0.5em;
  border-radius: 5px;
  padding: 4px;
  width: 200px;
  background-color: burlywood;

}
</style>
