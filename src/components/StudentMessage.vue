<template> 
      <div class="WelcomeOrByeStudents" v-if="student.name">

          <div class="alert alert-success " v-if="student.present">
              Welcome, {{student.name}}
          </div>

          <div class="alert alert-info" v-else>
              Goodbye, {{student.name}}. See you soon !
          </div>

      </div>
</template>

<script>
export default {
  // create component here
  name : 'StudentMessage',
  props: {
    student : Object
  }
}
</script>

<style scoped>
</style>
