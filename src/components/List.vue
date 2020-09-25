<template>
  <div>
    <div class="container rounded p-0 shadow-sm">
      <div id="add-task" class="list-group-item bg-light">
        <input type="text" class="form-control" placeholder="Adicionar Tarefa" v-model="title">
        <input type="datetime-local" class="form-control" placeholder="Adicionar Tarefa" v-model="date">
        <button class="btn btn-info shadow-sm">+</button>
      </div>
      <div class="">
        <div class="list-group-item bg-light text-left d-flex align-items-center  justify-content-between" v-for="(task) in taskList" v-bind:key="task.id">
          {{task.title}}
          <small>
            {{ new Date(task.date).toLocaleString('pt-br') }}
          </small>
            <button class="btn btn-danger shadow-sm rounded-circle">
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
        name: 'List',
        title: '',
        now: new Date().toLocaleString('pt-br'),
        date: '',
        taskList: [
        {title: 'Lavar a louça', date: '2020-06-25 13:00:00'}, 
        {title: 'Varrer a casa', date: '2020-06-20 08:00:00'}
        ]      
      }
    },
    components: {
      TrashIcon
    },
    methods: {
    }
  }
</script>

<style scoped>
input {
  margin-right: 5px;
}

#add-task {
  display: flex;
}

#add-task button {
  font-weight: 700;
}

</style>
