
<template>
<div class="container">
  <div class="card">
    <div class="card-header">
      <h4>
        Student
        <RouterLink to="/student/create" class="btn btn-primary float-end">
        Add Student
        </RouterLink>
      </h4>
    </div>
    <div class="card-body">
      <table class="table table bordered">
        <thead>
            <tr>
              <th>ID</th>
              <th>NAME</th>
              <th>COURSE </th>
              <th>EMAIL</th>
              <th>PHONE</th>
              <th>CREATED_AT</th>
              <th>ACTION</th>

            </tr>  
        </thead>
        <tbody  >
          <tr v-for="(student,index) in this.students" :key="index">
            <td>{{student.id}}</td>
            <td>{{student.name}}</td>
            <td>{{student.course}}</td>
            <td>{{student.address}}</td>
            <td>{{student.phone}}</td>
            <td>{{student.created_at}}</td>
            <td>
               <RouterLink to="/" class="btn btn-success ">
                   Edit
              </RouterLink>
              <button type="button" class="btn btn-primary ">Delete</button>
                
            </td>

          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>
</template>
<script>

import axios from 'axios'


export default {
  name : 'student',
  data(){
    return{
      student:[]
    }
  },
  mounted(){
    // console.log("i am here")
    this.getStudents();

  },
  methods:{

    getStudents(){

      axios.get('http://127.0.0.1:8000/api/getstudent').then(res =>{
        this.students = res.data.students
        // console.log(this.students);
      });
    }
  },
}
 
</script>

