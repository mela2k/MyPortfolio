<script setup>
import {
  Info,
  Volume2,
  Wifi,
  Github,
  Linkedin,
  FileUser,
  Youtube,
  Palette
} from "lucide-vue-next";
import { ref, onMounted, onUnmounted } from "vue";


// Show qr code panel
const showQR = ref(false);

function showQRToTrue() {
  showQR.value = true;
}

function showQRToFalse() {
  showQR.value = false;
}

// Show colormode panel
const showColorMode = ref(false);

function showColorModeToTrue() {
  showColorMode.value = true;
}

function showColorModeToFalse() {
  showColorMode.value = false;
}

// audio functions
const sound = new Audio("/sounds/voiceOver.mp3");

function playSound() {
  sound.currentTime = 0;
  sound.play();
}

// time functions
const time = ref("");

function updateTime() {
  const now = new Date();
  const hours = String(now.getHours()).padStart(2, "0");
  const minutes = String(now.getMinutes()).padStart(2, "0");
  time.value = `${hours}:${minutes}`;
  console.log(`${hours}:${minutes}`);
}

let intervalId;

onMounted(() => {
  updateTime();
  intervalId = setInterval(updateTime, 1000 * 60);
});
</script>

<template>
  <div id="backgroundImage">
    <div id="sideBar">
      <div id="topItems">
        <span class="icon" @click="showColorModeToTrue()">
          <Palette color="black" :size="42" />
        </span>

        <span class="icon">
          <Info color="black" :size="42" />
        </span>
      </div>

      <div id="bottomItems">
        <span id="wifiIcon" class="icon" @click="showQRToTrue()">
          <Wifi color="black" :size="42" />
        </span>

        <span id="volumeIcon" class="icon" @click="playSound()">
          <Volume2 color="black" :size="42" />
        </span>

        <span class="icon">
          <p id="time">{{ time }}</p>
        </span>
      </div>
    </div>

    <div v-if="showColorMode" id="colorModePanel">
      <div id="colorModeControls">
        <button id="closeIcon" @click="showColorModeToFalse()">
          <span class="icon">x</span>
        </button>
        <button id="minimizeIcon" @click="showColorModeToFalse()">
          <span class="icon">–</span>
        </button>
      </div>
      <h2>Choose a color theme:</h2>
      <div id="themeColors">
        <div id="themeOriginal" class="themeColor"></div>
        <div id="themeGreen" class="themeColor"></div>
        <div id="themeDark" class="themeColor"></div>
        <div id="themeBlue" class="themeColor"></div>
      </div>
    </div>

    <div v-if="showQR" id="qrPanel">
      <div id="qrControls">
        <button id="closeIcon" @click="showQRToFalse()">
          <span class="icon">x</span>
        </button>
        <button id="minimizeIcon" @click="showQRToFalse()">
          <span class="icon">–</span>
        </button>
      </div>
      <h2>CONNECT WITH ME</h2>
      <div id="qrBox">
        <img
          src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=mailto:j.chen2000_@hotmail.com"
          alt="QR code"
        />
      </div>
      <p>Scan de QR-code to send me an email</p>
    </div>

    <div id="informationBar">
      <div id="topBar">
        <span id="macbookControls">
          <button id="closeIcon">
            <span class="icon">x</span>
          </button>
          <button id="minimizeIcon">
            <span class="icon">–</span>
          </button>
          <button id="expandIcon">
            <span class="icon"><></span>
          </button>
        </span>
        <p>My projects</p>
      </div>

      <div id="title">
        <span>
          <p>Hello my name is Jun, nice to meet you! 👋🚀</p>
        </span>
      </div>

      <div id="linkBoxses">
        <div id="github" class="box">
          <Github color="black" :size="45" />
          <p>Mela2k</p>
        </div>
        <div id="profilePicture" class="box"></div>
        <div id="youtube" class="box">
          <Youtube color="white" :size="45" />
          <p>@Sogasptr</p>
        </div>
        <div id="linkedinBox" class="box">
          <Linkedin color="white" :size="45" />
          <p>My Linkedin</p>
        </div>
        <div id="empty" class="box"></div>
        <div id="resumeBox" class="box">
          <FileUser color="white" :size="45" />
          <p>Resume</p>
        </div>
      </div>

      <div id="underTitle">
        <span>
          <p>Cool projects I have built or attended:</p>
        </span>
      </div>

      <div id="projects">
        <div class="projectBox">
          <div id="techieChenIcon"></div>
          <div id="textBox">
            <div id="upperTitle">
              <p id="textRowOne">Techie Chen</p>
              <p id="textRowTwo">
                Techie Chen is a website that connects customers with it at
                home.
              </p>
            </div>

            <p id="checkTechieChen">Check website</p>
          </div>
        </div>
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

@keyframes spin {
  100% {
    transform: rotate(360deg);
  }
}

@keyframes slide-right {
   from {
    transform: translateY(-300px);
  }
  to {
    transform: translateY(0); 
  }
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
          font-size: 20px;
          font-weight: 700;
          color: black;
        }
      }

      .icon:hover {
        cursor: pointer;
      }
    }
  }

  #colorModePanel {
    background-color: rgba(217, 217, 217, 0.4);
    position: absolute;
    top: 2.5em;
    left: 10em;
    border-radius: 1em;
    animation-duration: 1s;
    animation-name: slide-right;
    
    #colorModeControls {
      gap: 5px;
      padding: 0.5em;
      border-top-left-radius: 1em;
      border-top-right-radius: 1em;
      background-color: rgba(0, 0, 0, 0.5);
      display: flex;


      button {
        display: flex;
        align-items: center;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        border: none;
        .icon {
          font-style: italic;
          font-weight: 700;
        }
      }

      button:hover {
        cursor: pointer;
      }

      #closeIcon {
        background-color: rgba(228, 56, 56, 0.5);
      }

      #minimizeIcon {
        background-color: rgba(247, 243, 8, 0.5);
      }
    }

    h2 {
      padding: 0.5em;
      padding-bottom: 0;
      color: black;
    }

    #themeColors {
      padding-top: 0;
      padding: 1em;
      display: flex;
      gap: 5px;
      .themeColor {
        width: 1.5em;
        height: 1.5em;
        border-radius: 50%;
        cursor: pointer;
      }
      #themeOriginal {
        background-color: rgba(217, 217, 217, 0.4);
      }
      #themeGreen {
        background-color: rgb(110, 172, 129);
      }
      #themeDark {
        background-color: rgb(71, 60, 60);
      }
      #themeBlue {
        background-color: rgb(157, 157, 240);
      }
    }
  }

  #qrPanel {
    bottom: 10em;
    left: 10em;
    border-radius: 1em;
    position: absolute;
    background-color: rgba(217, 217, 217, 0.4);
    color: black;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;

    animation-duration: 1s;
    animation-name: spin;
    #qrControls {
      padding: 0.5em;
      border-top-left-radius: 1em;
      border-top-right-radius: 1em;
      background-color: rgba(0, 0, 0, 0.5);
      width: 100%;
      left: 1em;
      display: flex;
      gap: 5px;
      button {
        display: flex;
        align-items: center;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        border: none;
        .icon {
          font-style: italic;
          font-weight: 700;
        }
      }

      button:hover {
        cursor: pointer;
      }

      #closeIcon {
        background-color: rgba(228, 56, 56, 0.5);
      }

      #minimizeIcon {
        background-color: rgba(247, 243, 8, 0.5);
      }
    }
    #qrBox {
      background-color: white;
      padding: 1em;
      border-radius: 10%;
      img:hover {
        transform: scale(1.05);
        cursor: pointer;
      }
    }

    h2 {
      font-weight: 600;
    }
    p {
      padding: 1em;
      font-size: 1em;
      font-weight: 400;
    }
  }

  #informationBar {
    height: 100vh;
    width: 50vw;
    background-color: rgba(217, 217, 217, 0.4);
    overflow-y: auto;
    #topBar {
      background-color: rgba(0, 0, 0, 0.5);
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      p {
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

    #title {
      padding-top: 2em;
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      span {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 60%;
        p {
          text-align: center;
          color: black;
          font-size: 2.5em;
          font-weight: 700;
        }
      }
    }

    #linkBoxses {
      padding-top: 2em;
      width: 100%;
      display: grid;
      grid-template-columns: repeat(3, 120px);
      grid-template-rows: repeat(2, 120px);
      gap: 24px;
      justify-content: center;
      align-items: center;

      .box {
        border-radius: 1em;
        width: 120px;
        height: 120px;
        background-color: rgb(255, 255, 255);
        border: 4px black solid;
      }

      #github {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        p {
          font-size: 1em;
          color: black;
          font-weight: 700;
        }
      }

      #profilePicture {
        background-image: url("../src/assets/profilePicture.jpg");
        background-size: cover;
        background-position: center;
      }

      #linkedinBox {
        background-color: rgb(25, 7, 124);
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        border: none;
        p {
          font-weight: 500;
        }
      }

      #youtube {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        background-color: red;
        p {
          font-weight: 400;
          color: white;
        }
      }

      #empty {
        background-color: aqua;
      }

      #resumeBox {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        background-color: black;
        p {
          font-weight: 700;
          color: white;
        }
      }
    }

    #underTitle {
      padding-top: 2em;
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      span {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 60%;
        p {
          text-align: center;
          color: black;
          font-size: 2.5em;
          font-weight: 700;
        }
      }
    }

    #projects {
      padding-top: 2.5em;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      .projectBox {
        width: 75%;
        display: flex;
        justify-content: center;
        height: 10em;
        #techieChenIcon {
          border-radius: 30%;
          height: 100%;
          width: 20%;
          background-image: url("../src/assets/techiechen.jpg");
          background-size: cover;
          background-position: center;
        }
        #textBox {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          padding: 1em;
          #upperTitle {
            color: black;
            #textRowOne {
              font-size: 20px;
              font-weight: 700;
            }
            #textRowTwo {
              font-size: 1em;
              font-weight: 500;
            }
          }
          #checkTechieChen {
            color: black;
            font-weight: 600;
            text-decoration: underline;
          }
        }
      }
    }
  }
}
</style>
