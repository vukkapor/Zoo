<template>
  <div>
    <table style="width:100%">
      <tr>
        <th>Species</th>
        <th>Name</th>
        <th>Date of birth</th>
      </tr>
      <tr v-for="(animal, index) in animals" :key="index">
        <td>{{animal.species}}</td>
        <td>{{animal.name}}</td>
        <td >{{animal.dateOfBirth || "Nepoznat"}}</td>
        <td> <button type="submit" @click="deleteAnimal(index)">Delete</button> </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      animals: [
        { species: "Wolf1", name: "Wolf1", dateOfBirth: "12.01" },
        { species: "Wolf2", name: "Wolf2", dateOfBirth: NaN },
        { species: "Wolf3", name: "Wolf3", dateOfBirth: "12.01" },
        { species: "Wolf4", name: "Wolf4", dateOfBirth: "12.01" },
        { species: "Wolf5", name: "Wolf5", dateOfBirth: "12.01" }
      ]
    };
  },

  methods: {
    deleteAnimal(index) {
      this.animals.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
