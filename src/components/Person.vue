<template>
  <tr>
    <td v-if="!editing">{{person.firstname}}</td>
    <td v-else><input type="text" placeholder="firstname" v-model="newPerson.firstname"></td>
    <td v-if="!editing">{{person.lastname}}</td>
    <td v-else><input type="text" placeholder="lastname" v-model="newPerson.lastname" ></td>
    <td v-if="!editing">{{person.age}}</td>
    <td v-else><input type="number" placeholder="age" v-model="newPerson.age"></td>
    <td v-if="!editing"><button class="pure-button" @click.prevent="editPerson">redigera</button></td>
    <td v-else><button class="pure-button" @click.prevent="addPerson">spara</button></td>
  </tr>
</template>

<script>
import db from '@/db'

export default {
  props: ['person'],
  data() {
    return {
      editing: false,
      newPerson: {
        firstname: "",
        lastname: "",
        age: 0
      }
    }
  },
  methods: {
    editPerson() {
      this.editing = true;
    },
    addPerson() {
      this.editing = false;
      console.log(this.newPerson);
      console.log(db);
      db.ref('people').child(this.person.id).update(this.newPerson)
    }
  },
  created() {
    this.newPerson.firstname = this.person.firstname;
    this.newPerson.lastname = this.person.lastname;
    this.newPerson.age = this.person.age;
  }
}
</script>

<style>

</style>
