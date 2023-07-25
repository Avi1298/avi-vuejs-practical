<template>
    <div class="parent-container">
      <FormComponent @form-submitted="handleFormSubmitted" />
      <TableComponent :formData="formData" />
    </div>
  </template>
  
  <script>
  import FormComponent from './MyForm.vue';
  import TableComponent from './DataTable.vue';
  
  export default {
    components: {
      FormComponent,
      TableComponent,
      
    },
    data() {
      return {
        formData: [],
      };
    },
    methods: {
      handleFormSubmitted(data) {
        this.formData.push(data);
      },
    },
  };
  </script>
  
  <style>
  .parent-container {
    display: flex;
    justify-content: space-between;
    margin-top: 40px;

  }

  .FormComponent, .TableComponent {
  flex: 1; 
  margin-right: 40px; 
}
  </style>
  