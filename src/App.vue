<template>
  <div id="App">

    <NewStudentForm></NewStudentForm>
    <student-message></student-message>
    <student-table></student-table>
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
  }
}
</script>

<style>

</style>
