<template>
    <div class="col-lg-6">
      <div class="small-table-container">
        <table class="data-table">
          <thead>
            <tr>
              <th>#</th>
              <th>Color</th>
              <th>Number</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(data, index) in formData" :key="index">
              <td>{{ index + 1 }}</td>
              <td>{{ data.item }}</td>
              <td>{{ data.value }}</td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="colored-balls">
        <div class="ball red">
          {{ getSumByColor("Red") }}
        </div>
        <div class="ball blue">
          {{ getSumByColor("Blue") }}
        </div>
        <div class="ball green">
          {{ getSumByColor("Green") }}
        </div>
      </div>
    </div>
  </template>

<script>
export default {
  props: {
    formData: Array,
  },
  computed: {
    getSumByColor() {
      return function (color) {
        const colorData = this.formData.filter((data) => data.item === color);
        const sum = colorData.reduce((acc, curr) => acc + curr.value, 0);
        return sum;
      };
    },
  },

};
</script>
  
  <style>
  .small-table-container {
    border: 3px solid #ccc;
    padding: 10px;
    max-width: 400px;
    margin: 0 auto;
  }
  
  .data-table {
    width: 100%;
    border-collapse: collapse;
  }
  
  .data-table th,
  .data-table td {
    padding: 8px;
    text-align: center;
    border: 1px solid #ccc;
  }
  
  .data-table th {
    background-color: #007bff;
    color: #fff;
  }
  
  .data-table tr:nth-child(even) {
    background-color: #f2f2f2;
  }
  
  .data-table tr:hover {
    background-color: #e0e0e0;
  }
  
  .colored-balls {
    display: flex;
    justify-content: space-between;
    margin: 20px;
  }
  
  .ball {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
  }
  
  .red {
    background-color: red;
  }
  
  .blue {
    background-color: blue;
  }
  
  .green {
    background-color: green;
  }
  </style>
  