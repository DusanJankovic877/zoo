<template>
  <div class="hello">
    <form @submit.prevent="addAnimal">
      <input type="text" v-model="name">
      <input type="text" v-model="sort">
      <input type="date" v-model="dateOfBirth">
      <select v-model="selectedSector">
        <option v-for="(sector, index) in sectors" :key="index">{{sector}}</option>
      </select>
      <button>add animal</button>
    </form>
    <table>
      <tr>
        <th>sort</th>
        <th>name</th>
        <th>date</th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
      <tr v-for="(animal, index) in AnimalList" :key="index">
        <td>{{animal.sort}}</td>
        <td>{{animal.name}}</td>
        <td v-if="animal.dateOfBirth">{{animal.dateOfBirth.toLocaleString()}}</td>
        <td v-else>unknown</td>
        <td>{{animal.selectedSector}}</td>
        <td><button @click="removeAnimal(index)">remove</button></td>
        <td><button @click="moveToTop(index, animal)">move to top</button></td>

        
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  // dateOfBirth: null,
  data() {
    return {
      name: '',
      sort: '',
      dateOfBirth: null,
      sectors: ['ptica', 'zmija', 'kopitari'],
      selectedSector: '',
      AnimalList: [
        {
          sort: 'Zebra',
          name: 'Mico',
          dateOfBirth: new Date(2020, 1, 6)
        },

                {
          sort: 'Tigar',
          name: 'Simba',
          dateOfBirth: new Date(2020, 1, 6)
        },
        {
          sort: 'Panda',
          name: 'Kung Fu',
          dateOfBirth: new Date(2020, 1, 6)
        },
        {
          sort: 'Zirafa',
          name: 'Milica',
          dateOfBirth: new Date(2020, 1, 6)
        },
        {
          sort: 'Slon',
          name: 'Dambo'
          
        }
      ]
    }
  },
  methods: {
    removeAnimal(index) {
      this.AnimalList.splice(index, 1);
    },
    moveToTop(index, animal){
      this.removeAnimal(index);
      this.AnimalList.unshift(animal);

    },
    addAnimal(){
      var newAnimal = {
        name: this.name,
        sort: this.sort,
        dateOfBirth: this.dateOfBirth,
        selectedSector: this.selectedSector
      }
      this.AnimalList.push(newAnimal);
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 30%;
  margin-left: 35%;
  margin-right: 35%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
form {
  display: flex;
  flex-direction: column;
    width: 30%;
  margin-left: 35%;
  margin-right: 35%;
}
</style>
