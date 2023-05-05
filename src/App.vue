<template>
  <div id="App">

    <NewStudentForm v-on:student-added="newStudnetAdded"> </NewStudentForm>
    <student-message v-bind:student="mostRecentStudents"></student-message>
    <student-table  
     v-bind:students = "students"
     v-on:student-arrived-or-left = "studentArrivedOrLeft"
     v-on:delete-student="deleteStudent"></student-table>
  </div>
</template>

<script>

import NewStudentForm from './components/NewStudentForm.vue'
import StudentMessage from './components/StudentMessage.vue'
import StudentTable from './components/StudentTable.vue'

export default {
  name: 'App',
  components: {
    NewStudentForm,
    StudentMessage,
    StudentTable
  },
  data(){
    return {
      students: [],
      mostRecentStudents: {}
    }
  },
  methods :{
    newStudnetAdded(student){
      this.students.push(student)
      this.students.sort(function(s1, s2){
        return s1.name.toLowerCase() < s2.name.toLowerCase()? -1: 1
      } )
    },
    studentArrivedOrLeft(student, present){

      let updateStudent = this.students.find( function(s){
        if(s.name === student.name && s.starID == student.starID){
          return true
        }
      })

      if(updateStudent){
        updateStudent.present = present
        this.mostRecentStudents = updateStudent

      }
    },
    deleteStudent(student){
      this.students = this.students.filter(function(s){
        if (s != student){
          return true
        }
      })
    }
  }
}
</script>

<style>

@import url(https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/css/bootstrap.min.css);

</style>
