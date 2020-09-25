<template>
  <div>
    <div class="container shadow p-0">
      <div id="add-task" class="list-group-item bg-light">
        <input type="text" class="form-control" placeholder="Adicionar Tarefa">
        <button class="btn btn-info">+</button>
      </div>
      <div class="">
        <div class="list-group-item bg-light text-left d-flex align-items-center  justify-content-between" v-for="(item, i) in taskList" v-bind:key="item">
          {{i + 1}}) {{item}}
          <svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-trash-fill" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd" d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1H2.5zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5zM8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5zm3 .5a.5.5 0 0 0-1 0v7a.5.5 0 0 0 1 0v-7z"/>
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: 'List',
        taskList: ['Lavar a louça', 'Varrer a casa']      
      }
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
