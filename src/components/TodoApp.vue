<template>
    <div class=" container text-center ">
       <h2 class="mt-5 text-center">ToDo App </h2>
      
       <div class="d-flex   mt-3">
          <input type="text" placeholder="Enter Task" v-model="task" class="form-control ">
          <input type="text" placeholder="Enter Status" v-model="status" class="form-control  ">

          <button class="btn btn-warning" @click="addTask" type="submit"> Add </button>
       </div>
          
          <table class="table table-bordered mt-5 text-center">
          <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(Task ,index) in Tasks" :key="index">
      <td>{{Task.name}}</td>
      <td>{{Task.status}}</td>
      <td>
          <button class="btn btn-success " @click="updateValue(index)" type="submit"> Edit</button>
          <button class="btn btn-warning" @click="deleteTask(index)" type="submit"> Delete</button>

      </td>
    </tr>
  </tbody>
</table>



     </div>
</template>

<script>

export default {
  name:" ",
  props : {
         msg  : String,
  },
  data () {
      return {
          task   : "",
          status : "",
          update : null,
          Tasks: [
              {
                name: "Read Emails",
                status:"uncompleted"
              },
              {
                name: "Validations In ERP",
                status:"Completed "
              }
          ]
          
      }
  },
  methods:{
      addTask(){
      if (this.task.length==='0'){
          return;
      }
    

      if(this.update === null){
           this.Tasks.push({
            name: this.task,
            status: this.status,
      })
      }
      else{
      
        this.Tasks[this.update].name=this.task
        this.Tasks[this.update].status=this.status

        this.update = null;
      }
      this.task=''
  
      },
      deleteTask(index){
        this.Tasks.splice(index,1)
      },
      updateValue(index){
         this.task=this.Tasks[index].name,
         this.status=this.Tasks[index].status,

         this.update=index;
      }
  }
}

</script>