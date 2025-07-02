<script setup>
import { Menu, Info, Volume2, Wifi } from 'lucide-vue-next';

</script>

<template>
  <div id="backgroundImage">
      <div id="sideBar">
        <div id="topItems">

          <span class="icon">
  <Menu 
    color="black"
    :size="60"
  />
</span>

<span class="icon">
  <Info 
    color="white"
    :size="42"
  />
</span>
          

         
        
        </div>

        <div id="bottomItems">
          <span class="icon">
            <Volume2
            color="black"
    :size="42"
            />
          </span>

          <span class="icon">
            <Wifi 
            color="black"
    :size="42"
            />

          </span>

          <span class="icon">
            <p id="time">14:40</p>
          </span>
         

        </div>
      </div>
  </div>
</template>

<style scoped>

html, body {
  height: 100%;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}


#backgroundImage {
  width: 100vw;
  height: 100vh;
  background-image: url('../src/assets/background.png');
  background-size: cover;
  background-position: center;

  #sideBar{
    height: 100vh;
    width: 7.5%;
    background-color: rgba(217, 217, 217, 0.4);
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    align-items: center;
    padding: 2em;

    #topItems, #bottomItems{
      display: flex;
      flex-direction: column;
      align-items: center;
      .icon{
        padding: 5px;
        #time{
          font: 30px;
          font-weight: 700;
          color: black;
        }
      }
    }
  }

}

</style>
