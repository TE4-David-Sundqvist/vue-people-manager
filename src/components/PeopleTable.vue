<template>
  <form class="pure-form" v-if="this.people">
    <table class="pure-table">
      <thead>
        <th>firstname</th>
        <th>lastname</th>
        <th>age</th>
        <th></th>
      </thead>
      <tbody>
        <Person v-for="(person, idx) in peopleAsArray" :key="idx" :person="person">
        </Person>
        <tr>
          <td><input type="text" placeholder="firstname" v-model="newPerson.firstname"></td>
          <td><input type="text" placeholder="lastname" v-model="newPerson.lastname"></td>
          <td><input type="number" placeholder="age" v-model="newPerson.age"></td>
          <td><button class="pure-button" @click.prevent="addPerson">add</button></td>
        </tr>
      </tbody>
    </table>
  </form>
</template>

<script>
import db from '@/db'
import Person from './Person.vue'

export default {
  name: "PeopleTable",
  data() {
    return {
      people: null,
      newPerson: {
        firstname: "",
        lastname: "",
        age: 0
      }
    }
  },
  methods: {
    addPerson() {
      db.ref('people').push(this.newPerson)
    }
  },
  computed: {
    peopleAsArray() {
      return Object.keys(this.people).map((k) => Object.assign({id: k}, this.people[k]))
    }
  },
  firebase: {
    people: db.ref('people')
  },
  components: { Person }
}
</script>

<style>
table {
  margin: 0 auto;
}
</style>
