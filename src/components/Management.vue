<template>
  <div class="hello">
    <h1 class="mt-4">{{ msg }}</h1>
    <b-overlay :show="loading" rounded="sm">
      <b-table class="custom-table m-5" small :fields="fields" :items="items" responsive="sm">
        <!-- A virtual column -->
        <template #cell(index)="data">
          {{ data.index + 1 }}
        </template>

        <template #cell(originalFile)="data">
          {{data.value}}
        </template>

        <template #cell(FileName)="data">
          {{data.value}}
        </template>

        <template #cell(FileExt)="data">
          {{data.value}}
        </template>

        <template #cell(FileSize)="data">
          {{data.value}}
        </template>

        <template #cell(Url)="data">
          {{data.value}}
        </template>

        <template #cell(Status)="data">
          {{data.value}}
          <b-icon v-if="data.value == 'Loaded'" icon="file-earmark-bar-graph-fill"></b-icon>
          <b-icon v-if="data.value == 'Processing'" icon="gear-wide-connected"></b-icon>
        </template>

        <template #cell(actions)="data">
          <b-button @click="saveRow(data.item)" class="save-btn" variant="outline-success">
            <b-icon icon="check-circle"></b-icon>
          </b-button>
        </template>
      </b-table>
    </b-overlay>
  </div>
</template>

<script>
// Library to make Querys too easy
// import axios from "axios";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      fields: [
          'index', // A virtual column that doesn't exist in items
          'originalFile',
          'FileName',
          'FileExt',
          'FileSize',
          'Url',
          'Status',
          'actions', // A virtual column that doesn't exist in items
        ],
      items: [],
      loading: false
    }
  },
  mounted() {
    this.loading = true;
    // AQUI SE CREA EL METODO GET PARA TRAERME TODA LA LISTA DE LA BASE DE DATOS Y ASIGNARSELA A this.items
    this.items = [
        { originalFile: 'File1.xlsx', FileName: 'File1.csv', FileExt: 'csv', FileSize: '450kb', Url: 'http://public1-url.csv', Status: 'Loaded' },
        { originalFile: 'File2.xlsx', FileName: 'File2.csv', FileExt: 'csv', FileSize: '451kb', Url: 'http://public2-url.csv', Status: 'Loaded'},
        { originalFile: 'File3.xlsx', FileName: 'File3.csv', FileExt: 'csv', FileSize: '452kb', Url: 'http://public3-url.csv', Status: 'Loaded' },
        { originalFile: 'File4.xlsx', FileName: 'File4.csv', FileExt: 'csv', FileSize: '453kb', Url: 'http://public4-url.csv', Status: 'Loaded' },
        { originalFile: 'File5.xlsx', FileName: 'File5.csv', FileExt: 'csv', FileSize: '454kb', Url: 'http://public5-url.csv', Status: 'Loaded' },
        { originalFile: 'File6.xlsx', FileName: 'File6.csv', FileExt: 'csv', FileSize: '455kb', Url: 'http://public6-url.csv', Status: 'Loaded' },
      ]
    this.loading = false;
  },
  methods: {
    async saveRow(row){
      this.loading = true;
      console.log(row);
      // AQUI SE IMPLEMENTA EL GUARDADO DE CADA UNA DE LAS FILAS DE LA TABLA CON AXIOS
      this.loading = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.save-btn {
  padding: 3px 3px 0px 3px;
}
.form-control {
  font-size: small;
  line-height: 1;
}
.custom-table {
  font-size: small;
}

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
</style>
