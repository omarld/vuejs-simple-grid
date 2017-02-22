<template>
  <div id="app">
    <h1>{{ msg }}</h1>
    <grid-component :data="gridData" :columns="gridColumns"></grid-component>
  </div>
</template>

<script>
    import MdlStyles from 'mdl/material.min.css';
    import GridComponent from './Components/GridComponent.vue'

    export default {
        name: 'app',
        data () {

            let columnNames= [
                {name: "Thumbnail", class:"mdl-data-table__cell--non-numeric", type:"image"},
                {name: "FileName", class:"mdl-data-table__cell--non-numeric", type:""},
                {name: "FileType", class:"mdl-data-table__cell--non-numeric", type:""},
                {name: "FileSize", class:"", type:""},
                {name: "TimeStamp", class:"mdl-data-table__cell--non-numeric", type:""}
            ];

            let sampleData = [
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                },
                {
                    "FileName": faker.name.findName(),
                    "FileType": faker.system.commonFileType(),
                    "FileSize": faker.random.number(),
                    "TimeStamp": faker.date.past(),
                    "Thumbnail": faker.image.food()
                }
            ];

            return {
                msg: 'VueJS Simple Grid',
                gridData: sampleData,
                gridColumns: columnNames,
                searchKey: ""
            }
        },
        components: {
            GridComponent
        }
    }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #f4f4f4;
}

h1, h2 {
  font-weight: normal;
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
</style>
