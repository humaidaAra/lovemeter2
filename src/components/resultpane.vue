<template>
  <p>{{ percentage }}</p>
  <div class="container1">
    <div class="spacer"></div>
     <div class="cilinder" :style="{width:measure}">

     </div>
  </div>
</template>

<script>

export default 
{
  props:
  {
    perc : Number
  },
    data(){
      return{
        percentage: null,
        measure: "0%"
      }
  },
  created()
    {
        this.emitter.on("getResult", data => {
          
            this.percentage = data;
            this.measure  = ""+this.percentage+"%";
         
        });
    }
}
</script>

<style scoped>
p
{
  position: absolute;
  left: 50%;
}
.container1
{
    position: absolute;
    /* background-color: darkslategrey; */
    border: solid 2px black;
    border-radius: 10px;
    width: 100%;
    height: 50%;
    display: flex;
    align-content: flex-start;
    align-items: center;
    justify-content: flex-start;

}
.spacer
{
  width: 10%;
  height: 10px;
}
.cilinder
{
    max-width: 80%;
    height: 20%;
    background-image: linear-gradient(to right,red,  rgb(255, 0, 242));
} 

</style>