<template lang="">
    <div class="h-screen bg-green-400 flex justify-center py-16">

        <div class="w-1/3">
            <div class="p-4 text-right shadow-2x1 rounded-t-lg bg-white">
                <p class="font-semibold text-gray-700 h-6">{{getOperation}}</p>
                <p class="font-bold text-9x1 text-gray-900 my-2">{{getResult}}</p>
            </div>
            <div class="grid grid-cols-4 grid-rows-5 shadow-2x1 rounded-t-lg">
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600 col-span-2" @click="acClicked" >AC</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600" @click="delClicked()" >DEL</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600" @click="charClicked('÷')" >÷</button>

                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('7')" >7</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('8')" >8</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('9')"  >9</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600" @click="charClicked('×')" >×</button>

                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('4')" >4</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('5')" >5</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('6')" >6</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600" @click="charClicked('-')" >-</button>

                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('1')" >1</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('2')" >2</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('3')" >3</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600" @click="charClicked('+')" >+</button>

                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 col-span-2 hover:bg-green-600"  @click="charClicked('0')" >0</button>
                <button class="h-16 text-xl text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="charClicked('.')" >.</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-500 border-gray-400 hover:bg-gray-600" @click="resultClicked()" >=</button>
            </div>

        </div>
    </div>
</template>
<script>
export default {
  name: "Calculate",
  data() {
    return {
        getOperation: '',
        getResult: '0',
    };
  },

  methods: {

    acClicked() {
        this.getResult = '0';
    },

    delClicked() {
        if (this.getResult.length > 1){
            this.getResult = this.getResult.substring(0 , this.getResult.length - 1); 
        } else {
            this.getResult = '0';
        }
    },

    charClicked(n) {
        if (this.getResult == '0') {
            this.getResult = n;
        } else {
            this.getResult += n;
        }
    },

    resultClicked(){
        let operation = this.getResult;
        this.getOperation = operation;

        operation = operation.replace('×' , '*');
        operation = operation.replace('÷' , '/');
        
        this.getResult = eval(operation);
    }
  }
};
</script>
<style scoped >

   button{
    border: 1px solid;
   }

</style>