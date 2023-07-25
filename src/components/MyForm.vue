<template>
    <div class="col-lg-6">
    <div class="small-form-container">
      <form @submit.prevent="submitForm">
        <label for="dropdown">Select Colour:</label>
        <select id="dropdown" v-model="selectedItem">
          <option value="Red">Red</option>
          <option value="Blue">Blue</option>
          <option value="Green">Green</option>
        </select>
  
        <br />
  
        <label for="inputField">Select Number:</label>
        <input type="text" id="inputField" v-model="inputValue" />
  
        <br />
  
        <div class="button-container">
          <button type="submit">Submit</button>
          <button type="button" @click="clearForm">Clear</button>
        </div>
      </form>
    </div>
</div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selectedItem: "",
        inputValue: "",
      };
    },
    methods: {
      submitForm() {
        this.$emit("form-submitted", {
          item: this.selectedItem,
          value: this.inputValue,
        });
      },
      clearForm() {
        this.selectedItem = "";
        this.inputValue = "";
      },
    },
  };
  </script>
  
  <style>
  .small-form-container {
    border: 3px solid #ccc;
    padding: 10px;
    display: grid;
    max-width: 300px; 
    margin: 0 auto;
  }
  
  form {
    display: flex;
    flex-direction: column;
  }
  
  label {
    font-weight: bold;
    margin-bottom: 8px;
  }
  
  select,
  input {
    margin-bottom: 16px;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .button-container {
    display: flex;
    justify-content: space-between;
  }
  
  button {
    padding: 8px 16px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    color: #fff;
  }
  
  button[type="submit"] {
    background-color: #007bff;
  }
  
  button[type="submit"]:hover {
    background-color: #0056b3;
  }
  
  button[type="button"] {
    background-color: #dc3545;
  }
  
  button[type="button"]:hover {
    background-color: #c82333;
  }
  </style>
  