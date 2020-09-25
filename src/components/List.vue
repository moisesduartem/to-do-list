<template>
  <div>
    <div class="container rounded p-0 shadow-sm">
      <h4 class="text-muted">Lista de Tarefas - {{now.split(' ')[0]}}</h4>
      <small>
        <a href="http://github.com/moisesduartem/to-do-list">github.com/moisesduartem</a>
      </small>
      <hr>
      <div class="list-group-item bg-light p-3">
        <input type="text" class="form-control mb-2" placeholder="Nome do compromisso" v-model="newTitle">
        <input type="datetime-local" class="form-control mb-2" v-model="newDate">
        <input v-on:click="addTask" class="btn btn-block btn-info shadow-sm" type="button" value="Adicionar">
        <input v-on:click="clearTaskList" class="btn btn-block btn-success shadow-sm" type="button" value="Limpar">
      </div>
      <div class="task list-group-item text-left d-flex align-items-center  justify-content-between" v-for="(task, i) in taskList" v-on:click="concludeTask(i)" :key="task.id">
        <input type="checkbox" v-model="taskList[i].concluded" :id="i">
        <span class="task-title" v-if="taskList[i].concluded"><strike>{{task.title}}</strike></span>
        <span class="task-title" v-else="">{{task.title}}</span>
        <small>
          {{ new Date(task.date).toLocaleString('pt-br') }}
        </small>
        <button v-on:click="removeTask(i)" class="btn btn-danger shadow-sm rounded-circle">
          <TrashIcon />
        </button>
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
        taskList: []      
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
        if ( this.taskList[i] ) {
          this.taskList[i].concluded = !this.taskList[i].concluded;
        }
      },
      clearTaskList() {
        this.taskList = [];
      }
    }
  }
</script>

<style scoped="">

.container {
  max-width: 420px;
}

.task {
  transition: all .3s;
}

.task .task-title {
  font-size: 14px;
}

.task concluded :hover {
  background-color: #f5fff5;
}

</style>
