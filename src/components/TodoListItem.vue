<template>
  
    <div class="flex flex-wrap items-center shadow rounded-2xl my-5 py-3 pt-z pr-4 pb-3">
      
      <label class="accent-pink-500 pl-4 pt-1.5"> 
        <input type="checkbox" > <!--checkbox-->
      </label>  

      <div class="pr-2 font-normal text-gray-900 rounded-3xl rounded-l-lg  ml-2 pt-1">
   {{ item.text }}
      </div>
      <div class="ml-auto space-x-2">

        <button  
          type="button"
          class="appearance-none font-bold bg-green-600 rounded text-white px-3 py-1 text-xs focus:outline-none focus:ring hover:bg-green-500"
          @click="handleEditClick(item)"  
        >
        {{teste == item.id ? "Ok" : "Editar"}}

        </button>
        <button
          type="button"
          class="appearance-none font-bold bg-red-900 rounded text-white px-3 py-1 text-xs focus:outline-none focus:ring hover:bg-red-600"
          @click="handleDeleteClick"
        >
          Excluir
          
        </button>

      </div>
    </div>
  </template>
  
  <script>

  import { computed } from "vue";   //e 'computed'
  
  export default {

   data: () => ({
     teste: []
     }),
  
    props: {
      item: {
        type: Object,
        required: true,
      },
      batata: null
    },

    methods: {
        handleEditClick(v) {
        this.teste = v.id
        this.$emit("edit", v);
      }
    },

    watch: {
      batata(){
        debugger
      }
    },
  
    setup(props, { emit }) {
      const formattedTimestamp = computed(() => {
        const date = new Date(props.item.timestamp);
        
        return `${date.toLocaleDateString()} ${date.toLocaleTimeString()}`;

        components: {CheckboxEvent}

      });
      
     
  
      function handleDeleteClick() {
        emit("delete", props.item);
      }

      return {

        formattedTimestamp,
        handleDeleteClick,
      };
    },
  };

  </script>