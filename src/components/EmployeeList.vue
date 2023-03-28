<template>
    <div>
      <h1>Employee List</h1>
      <table border="1px">
        <tr>
            <td>Name</td>
            <td>Salary</td>
            <td>Age</td>
        </tr>
        <tr v-for="item in list" v-bind:key="item.id">
            <td>{{item.employee_name}}</td>
            <td>{{item.employee_salary}}</td>
            <td>{{item.employee_age}}</td>
        </tr>
      </table>
    </div>
  </template>
  
  <script>
  import { createApp } from 'vue';
  import axios from 'axios';
  import VueAxios from 'vue-axios';
  
  const app = createApp({});
  
  app.use(VueAxios, axios);
  
  export default {
    name: "EmployeeList",
    data()
    {
        return {list:undefined}
    },
    mounted() {
      app.config.globalProperties.axios.get('https://dummy.restapiexample.com/api/v1/employees')
        .then((resp) => {
            this.list=resp.data.data;
          console.warn(resp.data.data);
        });
    },
  };
  </script>
  