<template>
  <div>
    <form @submit.prevent="addAnimal">
      <div>
        <label for="species">Species</label>
        <input type="text" id="species" v-model="newAnimal.species">
      </div>
      <div>
        <label for="name">Name</label>
        <input type="text" id="name" v-model="newAnimal.name">
      </div>
      <div>
        <label for="dateOfBirth">Date of birth</label>
        <input type="text" id="dateOfBirth" v-model="newAnimal.dateOfBirth">
      </div>
      <div>
        <select v-model="newAnimal.animalType">
          <option disabled value>Please select one</option>
          <option v-for="(type, index) in animalTypes" :key="index">{{type}}</option>
        </select>
        <span>Selected: {{ selected }}</span>
      </div>
      <div>
        <button type="submit">Add a new animal</button>
      </div>
    </form>
    <table style="width:100%">
      <tr>
        <th>Species</th>
        <th>Name</th>
        <th>Date of birth</th>
        <th>Animal Type</th>
      </tr>
      <tr v-for="(animal, index) in animals" :key="index">
        <td>{{animal.species}}</td>
        <td>{{animal.name}}</td>
        <td>{{animal.dateOfBirth || "Nepoznat"}}</td>
        <td>{{animal.animalType}}</td>
        <td>
          <button type="submit" @click="deleteAnimal(index)">Delete</button>
        </td>
        <td>
          <button type="submit" @click="moveToTop(index)">Move to top</button>
        </td>
      </tr>
    </table>
    <table style="width:100%">
      <tr v-for="(animalType, index) in animalTypes" :key="index">
        <td>{{animalType}}</td>
        <td>
          <button type="submit" @click="showAnimalsOfThatType(animalType)">Show animals</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newAnimal: this.defaultAnimal(),

      animals: [
        {
          species: "Wolf1",
          name: "Wolf1",
          dateOfBirth: "12.01",
          animalType: "ptice"
        },
        {
          species: "Wolf2",
          name: "Wolf2",
          dateOfBirth: NaN,
          animalType: "ptice"
        },
        {
          species: "Wolf3",
          name: "Wolf3",
          dateOfBirth: "12.01",
          animalType: "nesto"
        },
        {
          species: "Wolf4",
          name: "Wolf4",
          dateOfBirth: "12.01",
          animalType: "nesto"
        },
        {
          species: "Wolf5",
          name: "Wolf5",
          dateOfBirth: "12.01",
          animalType: "sisari"
        }
      ],

      animalTypes: ["ptice", "sisari", "svasta"]
    };
  },

  methods: {
    defaultAnimal() {
      return {
        species: "",
        name: "",
        dateOfBirth: "",
        animalType: "unknown"
      };
    },
    deleteAnimal(index) {
      this.animals.splice(index, 1);
    },

    moveToTop(index) {
      this.animals.unshift(this.animals[index]);
      this.animals.splice(index + 1, 1);
    },

    addAnimal() {
      this.animals.push({ ...this.newAnimal });
      this.newAnimal = this.defaultAnimal();
    },
    showAnimalsOfThatType(animalType) {
      var animalsOfType = this.animals.filter(animals => animals.animalType === animalType).map(animal => animal.name);
      alert(animalsOfType.join(', '))
    }
  }
};
</script>

<style>
</style>
