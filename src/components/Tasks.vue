<template>
  <div class="container">
    <div class="row">
      <div class="col-auto" v-for="task in tasks" :key="task.id">
        <div
          class="card text-white bg-dark mb-3 border border-white"
          style="width: 15rem">
          <div class="card-body">

            <p>
              <label :class="{ resolvido: task.isCompleted }"
                >Tarefa: {{ task.task }}
              </label>
            </p>
            <label :class="{ resolvido: task.isCompleted }">
              Finalizada:
              <input
                :checked="task.isCompleted"
                type="checkbox"
                @click="resolvido(task.id)"
              />
            </label>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListaTarefas",
  props: {
    tasks: [],
  },
  data() {
    return {
      tasksArray: []
    };
  },
  methods: {
    resolvido(taskId) {
      for (const task of this.tasks) {
        if (task.id === taskId) {
          task.isCompleted = !task.isCompleted;
        }
      }
    },

    removeTask(taskId) {
      this.$emit('clicked', taskId)
    },
  },
};
</script>

<style scoped>

ul {
  list-style: none;
}
.card {
  margin-bottom: 0.5em;
  border-radius: 10px;
  font-weight: 600;
  opacity: 0.9;
}
.card:hover{
  opacity: 1;
  -moz-transform: scale(1.05);
	-webkit-transform: scale(1.05);
	transform: scale(1.05);
  transition: all 0.5s;
}

.container {
  color: #070707;
  padding: 5em;
  padding-top: 1em;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  background: rgb(226, 226, 224);
}
.resolvido {
  text-decoration: line-through;
  opacity: 0.5;
}
.naoresolvido {
  text-decoration: none;
}
.botao_deletar {
  margin-top: 5px;
}
</style>