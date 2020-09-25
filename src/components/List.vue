<template>
  <div>
    <div class="container rounded p-0 shadow-sm">
      <div id="add-task" class="list-group-item bg-light">
        <input type="text" class="form-control" placeholder="Adicionar Tarefa">
        
      </div>
      <div class="">
        <div class="list-group-item bg-light text-left d-flex align-items-center  justify-content-between" v-for="(task) in taskList" v-bind:key="task">
          {{task}}
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
        taskList: ['Lavar a louça', 'Varrer a casa']      
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
