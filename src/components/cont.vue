<template>
  
   <div class="container">
    <form action="" class="col-12 h-75 d-flex justify-content-center align-items-center">
      <div> 
          <label id="lbl1" for="inp1" >Enter person 1 name: </label>
          <input v-model="inp1" class="inp1" type="text" />
          <label id="lbl2" for="inp2" >Enter person 2 name: </label>
          <input v-model="inp2" class="inp2" ref="inp2" type="text">
          <button class="btn" @click="check">Test!</button>
      </div>
    </form>
  </div>
</template>

<script>
export default 
{
  
  data(){
    return{
      inp1:'',
      inp2:''
    }
  },
  methods:
  {
    generateRand()
    {
      var x = Math.floor(Math.random()*(100)+1); //between 0 and 100
      return x;
    },
    
      check(e)
      {
        e.preventDefault();
      
        if(this.inp1.toLowerCase() == "" || this.inp2.toLowerCase() == "")
        {
          alert("you have nothin ma man");
          
          return;
        }
        else if(this.inp1.toLowerCase() == this.inp2.toLowerCase())
        {
           alert("mn xomm zor xoshawe, 3ashqi xomm, emmmm owww")
           this.inp1="";
           this.inp2="";
           return;
        }
        else
        {
          this.emitter.emit("getResult", this.generateRand());
          //  this.inp1="";
          //  this.inp2="";
        }
      }
  }
}
</script>

<style scoped>
    .btn
    {
      width: 100px;
      height: 40px;
      left: 80%;
      top: 35%;
    }
    form > div > input,label,button
    {
      position: absolute;
    }
    #lbl1
    {
      left: 2%;
      top: 40%
    }
    .inp1
    {
      top: 35%;
      left: 15%;
    }
    #lbl2
    {
      left: 40%;
      top: 40%;
    }
    .inp2
    {
      left: 53%;
      top: 35%
    }
    label
    {
        font-size: 20px;
    }
    .container
    {
        width:100%;
        height: 30vh;
        /* background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(43,43,43,1) 100%); */
        border: solid 2px black;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    input
    {
      width: 260px;
      height: 30px;
      text-rendering: geometricPrecision;
      border-radius: 5 px;
    }
    form
    {
      width: 100%;
      height: 50%;
    }
    form > div
    {
      width: 100%;
      height: 100%;
      margin-left: 0px;
      position: relative;
    }
</style>