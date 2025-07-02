<script setup>
import { Menu, Info, Volume2, Wifi } from "lucide-vue-next";
</script>

<template>
  <div id="backgroundImage">
    <div id="sideBar">
      <div id="topItems">
        <span class="icon">
          <Menu color="black" :size="60" />
        </span>

        <span class="icon">
          <Info color="white" :size="42" />
        </span>
      </div>

      <div id="bottomItems">
        <span class="icon">
          <Volume2 color="black" :size="42" />
        </span>

        <span class="icon">
          <Wifi color="black" :size="42" />
        </span>

        <span class="icon">
          <p id="time">14:40</p>
        </span>
      </div>
    </div>

    <div id="informationBar">
      <div id="topBar">
        <span id="macbookControls">
          <button id="closeIcon">
            <span class="icon">x</span>
          </button>
          <button id="minimizeIcon">
            <span class="icon">-</span>
          </button>
          <button id="expandIcon">
            <span class="icon"><></span>
          </button>
        </span>
        <p>My projects</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
}

#backgroundImage {
  width: 100vw;
  height: 100vh;
  background-image: url("../src/assets/background.png");
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: center;
  position: relative;

  #sideBar {
    position: absolute;
    left: 0;
    height: 100vh;
    width: 7.5%;
    background-color: rgba(217, 217, 217, 0.4);
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    align-items: center;
    padding: 2em;

    #topItems,
    #bottomItems {
      display: flex;
      flex-direction: column;
      align-items: center;
      .icon {
        padding: 5px;
        #time {
          font: 30px;
          font-weight: 700;
          color: black;
        }
      }
    }
  }

  #informationBar {
    height: 100vh;
    width: 50vw;
    background-color: rgba(217, 217, 217, 0.4);
    #topBar {
      background-color: rgba(0, 0, 0, 0.5);
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      p{
        font-size: 2em;
        font-weight: 700;
      }

      #macbookControls {
        position: absolute;
        left: 1em;
        display: flex;
        gap: 5px;
        button {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 22px;
          height: 22px;
          border-radius: 50%;
          border: none;
          .icon {
            font-style: italic;
            font-weight: 700;
          }
        }

        #closeIcon {
          background-color: rgba(228, 56, 56, 0.5);
        }

        #minimizeIcon {
          background-color: rgba(247, 243, 8, 0.5);
        }

        #expandIcon {
           background-color: rgba(64, 231, 14, 0.5);
        }
      }
    }
  }
}
</style>
