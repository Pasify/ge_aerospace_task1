<script setup>
import { ref } from 'vue'
const IMAGE_URL="https://mms.businesswire.com/media/20240719740240/en/2190719/22/ge_aerospace_logo.jpg"

let num1= ref(0)
let num2= ref(0)
let result = ref(null)
let computedStatus=  ref(false)

function computeSum (){
  result.value=num1.value * num2.value
  if(!computedStatus.value){
    computedStatus.value=true;
  }
};
function reset () {
  computedStatus.value=false;
  num1.value=0;
  num2.value=0;
}
</script>

<template>
  <div class="container">
    <div class="header">
      <h1>Compute Product </h1>
      <div class="image_container">

      <img :src="IMAGE_URL" alt="ge_aerospace_logo"/>
    </div>
     
    </div>
    <div class="inputs">
      <input type="number" v-model="num1" max="5" :disabled="computedStatus" />
     <input type="number" v-model="num2" max="5" :disabled="computedStatus"/> 
    </div>
    <hr/>
    <div class="output">
      <div v-if="computedStatus" class="reset"> 
        <p>The sum of {{num1}} and {{num2}} is {{result}} </p>
        <button @click="reset">Reset</button>
      </div>
      <div v-else>
        <button @click="computeSum">Compute </button>
      </div>
    </div>

  </div>
</template>
<style >

*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
:root{
  --main-color: gainsboro;
  --seconary-color:whitesmoke;
  --ouline-color:gray;
  --text-color: black

}
html{
  font-size: 62.5%;
}
body{
  background-color: var(--main-color);
  width: 100vw;
  height: 100vh;
  box-sizing: border-box;
  display: grid;
  place-items: center;

}
.container{
    display: flex;
    flex-direction: column;
    justify-items: center;
    align-content: center;
    background-color: var(--seconary-color);
    outline: 1px solid var(--ouline-color);
    padding: 2rem;
    gap: 2rem;
    width: 100%;
    border-radius: .5rem;
    .header{
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: .5rem;
      .image_container{
        width: auto;
        height: 6rem;
       img{
        height: 100%;
        width: 100%;
        object-fit: contain;
      } 
      }
      
    }
    .inputs{
      display: flex;
      flex-direction: column;
      gap:1rem;
      input{
        outline: 1px solid var(--ouline-color);
        border: 0;
        padding: 1.5rem;
        border-radius: .5rem;
        font-size: 1.5rem;
        caret-color: var(--ouline-color);

      }
    }
    .output{
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: stretch;
      gap: 1rem;
      font-size: 1.5rem;
      width: 100%;
     
      .reset{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1rem;
        
      }
      button{
        padding: 1rem;
        border-radius: .5rem;
        border: none;
        background-color: var(--main-color);
        outline: 1px solid var(--ouline-color);
        width: 100%;
        color: var(--text-color)
      }

    }
}
</style>
