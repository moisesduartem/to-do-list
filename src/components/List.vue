<template>
  <div>
    <div class="container rounded p-0 shadow-sm">
    <h4 class="">Lista de Tarefas - {{now.split(' ')[0]}}</h4>
    <hr>
      <div id="add-task" class="list-group-item bg-light">
        <input type="text" class="form-control" placeholder="Adicionar Tarefa" v-model="newTitle">
        <input type="datetime-local" class="form-control" placeholder="Adicionar Tarefa" v-model="newDate" value="2020-12-25T08:00">
        <button v-on:click="addTask" class="btn btn-info shadow-sm">+</button>
      </div>
      <div class="">
        <div class="task list-group-item text-left d-flex align-items-center  justify-content-between" v-for="(task, i) in taskList" v-on:click="concludeTask(i)" v-bind:key="task.id">
          <span class="task-title">{{task.title}}</span>
          <small>
            {{ new Date(task.date).toLocaleString('pt-br') }}
          </small>
          <button v-on:click="removeTask(i)" class="btn btn-danger shadow-sm rounded-circle">
            <TrashIcon />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import TrashIcon from './icons/TrashIcon';
  export default {
    data() {
      return {
        newTitle: '',
        newDate: '',
        name: 'List',
        taskList: [
        {title: 'Lavar a louça', date: '2020-06-25 13:00:00', concluded: false}, 
        {title: 'Varrer a casa', date: '2020-06-20 08:00:00', concluded: false},
        ]      
      }
    },
    computed: {
        now() {
          const date = new Date();
          return `${date.toLocaleString('pt-br')}`
        }
    },
    components: {
      TrashIcon
    },
    methods: {
      addTask() {
        if (this.newTitle && this.newDate) {
          this.taskList.push({ 
            title: this.newTitle, 
            date: this.newDate, 
            concluded: false });
        }
        this.newTitle = '';
        this.newDate = '';
      },
      removeTask(i) {
        this.taskList.splice(i, 1);
      },
      concludeTask(i) {
        this.taskList[i].concluded = !this.taskList[i].concluded;
      }
    }
  }
</script>

<style>
input {
  margin-right: 5px;
}

#add-task {
  display: flex;
}

#add-task button {
  font-weight: 700;
}

.task {
  transition: all .3s;
}

.task .task-title {
  font-size: 14px;
}

.task:hover {
  background-color: #f5fff5;
}

</style>
