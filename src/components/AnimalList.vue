<template>
  <div class="hello">
    <table>
      <tr>
        <th>sort</th>
        <th>name</th>
        <th>date</th>
      </tr>
      <tr v-for="(animal, index) in AnimalList" :key="index">
        <td>{{animal.sort}}</td>
        <td>{{animal.name}}</td>
        <td v-if="animal.dateOfBirth">{{animal.dateOfBirth.toLocaleString()}}</td>
        <td v-else>unknown</td>
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
</style>
