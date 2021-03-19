<template>
  <div class="view">
    <div class="view-title">
      <h2>DATATHON</h2>
      <hr />
    </div>

    <div class="content">
        <div class="content__title">
            <h2>INPUTS</h2>
        </div>

        <div class="content__inputs" v-for="(item, index) in inputItems" :key="index" >
            <div class="weight">
                <label for="">Weight</label>
                <input
                    v-model="inputItems[index].weight"
                    class="input input-weight"
                    type="text"
                    aria-haspopup="true"
                    placeholder="Type Weight..."
                />
            </div>

            <div class="density">
                <label for="">Density</label>
                <input
                    v-model="inputItems[index].density"
                    class="input input-density"
                    type="text"
                    aria-haspopup="true"
                    placeholder="Type Density..."
                />
            </div>

            <div class="cubic-feet">
                <label for="">Cubic Feet</label>
                <input
                    v-model="inputItems[index].cubic_feet"
                    class="input input-cubic"
                    type="text"
                    aria-haspopup="true"
                    placeholder="Type Cubic Feet..."
                />
            </div>
        </div>
    </div>

    <div>
        <button class="button-add" @click="addInput()">ADD INPUT</button>

        <button class="button-calculate" @click="calculate()">CALCULATE</button>
    </div>

    <div class="table-content">
        <b-table striped hover :items="resultItems" head-variant="dark"></b-table>
    </div>


  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "view",
  components: {

  },
  created(){
      this.inputItems.push({weight: 0, density: 0, cubic_feet: 0});
  },
  data(){
    return {
        inputItems: [],
        resultItems: [
          { lenght: 40, width: 'Dickerson', height: 'Macdonald', hu_count: 'Macdonald' },
          { lenght: 21, width: 'Larsen', height: 'Shaw', hu_count: 'Macdonald' },
          { lenght: 89, width: 'Geneva', height: 'Wilson', hu_count: 'Macdonald' },
          { lenght: 38, width: 'Jami', height: 'Carney', hu_count: 'Macdonald' }
        ]
    }
  },
  methods:{
      addInput(){
         this.inputItems.push({weight: 0, density: 0, cubic_feet: 0}); 
      },

      calculate(){
        axios.get('/user?ID=12345')
        .then(function (response) {
          // handle success
          console.log(response);
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
        .then(function () {
          // always executed
        });
      }
  }
};
</script>

<style lang="scss" scoped>

.view{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}


.view-title {
  padding-top: 30px;
  width: 100%;
  background-color: #2d3688;
  box-shadow: 0 0 0 0.5rem rgba(#000000, 0.5);
  position: sticky;
  top: 0;
  
  h2{
      padding: 10px;
      color: white;
  }

}

.content{
    margin: 40px;
    width: 80%;
    border-radius: 20px;
    border: 1px solid;
    border: 1px solid rgb(107, 107, 107);
    box-shadow: 1px 1px 1px 1px rgba(#000, 0.1);

    &__title{
       background-color: #2d3688; 
       border-top-left-radius: 20px;
       border-top-right-radius: 20px;

       h2{
           padding: 20px;
           color: white;
       }
    }

    &__inputs{
        border:2px solid #2d3688;
        padding: 20px;
        margin: 10px;
        border-radius: 20px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
}

.weight{
    display: flex;
    flex-direction: column;
}

.density{
    display: flex;
    flex-direction: column;
}

.cubic-feet{
    display: flex;
    flex-direction: column;
}

.input{  
  outline: none;
  border-radius: 8px;
  padding: 10px;
  margin-top: 0px;
  width: 100%;
  border: 2px solid rgb(107, 107, 107);

  &:hover {
    border: 2px solid rgba(#000, 0.1);
  }
}

.table-content{
    padding: 30px;
    width: 80%;
}

::v-deep thead{
    th{
        border: none;
        background-color: #2d3688 !important;
    }   
}

.button-add{
    width: 100%;
    padding: 10px;
    background-color: #2d3688;
    border: none;
    color: white;
    border-radius: 20px;
}

.button-calculate{
  margin-top: 10px;
  width: 100%;
  padding: 10px;
  background-color: #2d3688;
  border: none;
  color: white;
  border-radius: 20px;
}
</style>