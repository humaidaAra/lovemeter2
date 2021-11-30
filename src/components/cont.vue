<template>
  
   <div class="container">
    <form action="" class="col-12 h-75 d-flex justify-content-center align-items-center">
      <div> 
          <label id="lbl1" for="inp1" >Enter person 1 name: </label>
          <input v-model="inp1" class="inp1" type="text" />
          <label id="lbl2" for="inp2" >Enter person 2 name: </label>
          <input v-model="inp2" class="inp2" ref="inp2" type="text">
          <button :disabled='disabl' class="btn btn-primary" @click="check">Test!</button>

          <label class="male1lbl" for="male1">Male</label>
          <input v-model="gen1" class="male1" type="radio" @change="checkGhey" name="gend1" value="male" />

          <label class="fmale1lbl" for="female1">fMale</label>
          <input v-model="gen1" class="female1" type="radio" @change="checkGhey" name="gend1" value="fMale" />


          <label class="male2lbl" for="male2">Male</label>
          <input v-model="gen2" class="male2" type="radio" @change="checkGhey" name="gend2" value="male" />

          <label class="fmale2lbl" for="female2">fMale</label>
          <input v-model="gen2" class="female2" type="radio" @change="checkGhey" name="gend2" value="fMale"/>

      </div>
    </form>
    <img class="caughtGhey" src="../assets/ghey.jpg" v-show="isGhey" alt="" />
  </div>
</template>
<script>
import Swal from 'sweetalert2'
export default 
{
  
  data(){
    return{
      inp1:'',
      inp2:'',
      gen1: '',
      gen2: '',
      isGhey: false,
      disabl:  false
    }
  },
  methods:
  {
    checkGhey(e)
    {
      e.preventDefault();

        if(!(this.gen1 == "" || this.gen2 == ""))
        {
          if(this.gen1 == this.gen2)
          {
              const imagePath = require("@/assets/ghey.jpg");
            Swal.fire(
            {
              title: "GHEY",
              imageUrl: imagePath,
              imageWidth: 400,
              imageHeight: 200,
            });
          this.disabl = true
          return;
          }
          this.disabl= false
        }
        else
        {
          this.disabl=false;
        }
    },
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
        Swal.fire(
        {
          title: 'empty',
          text: 'enter both field please',
          icon: 'error',
          width: 400
        })
        
        return;
      }
      else if(this.inp1.toLowerCase() == this.inp2.toLowerCase())
      {
         Swal.fire(
           {
             title: "we got a radical self lover psycho here!",
             text: "\"mn xomm zor xoshawe, 3ashqi xomm, emm oww\" ",
             width: 400,
           }
         );
          this.inp1="";
          this.inp2="";
          return;
      }
      else
      {
        this.emitter.emit("getResult", this.generateRand());
      }
    }
  }
}
</script>

<style scoped>
  .male1, .male1lbl, .male2, .male2lbl, .female1, .fmale1lbl, .female2, .fmale2lbl
  {
    position: absolute;
    width: 20px;
  }
  .male1
  {
    top: 86%;
    left: 15%;
  }
  .male1lbl
  {
    top: 90%;
    left: 17%
  }
  .female1
  {
    top: 86%;
    left: 25%
  }
  .fmale1lbl
  {
    top: 90%;
    left: 27%;
  }
  .male2
  {
    top: 86%;
    left: 53%;
  }
  .male2lbl
  {
    top: 90%;
    left: 55%;
  }
  .female2
  {
    top: 86%;
    left: 63%;
  }
  .fmale2lbl
  {
    top: 90%;
    left: 65%;
  }

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
        height: 50vh;
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