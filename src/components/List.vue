<template>
  <div>
    <div class="container rounded p-0 shadow-sm">
      <div id="add-task" class="list-group-item bg-light">
        <input type="text" class="form-control" placeholder="Adicionar Tarefa">
        <Button>+</Button>
      </div>
      <div class="">
        <div class="list-group-item bg-light text-left d-flex align-items-center  justify-content-between" v-for="(task) in taskList" v-bind:key="task.id">
          {{task.title}}
          <small>
            {{ new Date(task.date).toLocaleString('pt-br') }}
          </small>
          <Button color='danger' circle=true>
            <TrashIcon />
          </Button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Button from './Button';
  import TrashIcon from './icons/TrashIcon';
  export default {
    data() {
      return {
        name: 'List',
        taskList: [
        {title: 'Lavar a louça', date: '2020-06-25 13:00:00'}, 
        {title: 'Varrer a casa', date: '2020-06-20 08:00:00'}
        ]      
      }
    },
    components: {
      Button,
      TrashIcon
    }
  }
</script>

<style scoped>
#add-task {
  display: flex;
}

#add-task button {
  margin-left: 5px;
  font-weight: 700;
}

</style>
