<script setup>
import { defineComponent } from "vue";
import { music } from "@/store/index";
import { storeToRefs } from "pinia";

import ProgressLine from "./components/progress-line";
import Information from "./components/information";
import AudioControls from "./components/audio-controls";

const { getIsPaused, getCurrentSchedule, getMusicDescription, getIsToggleImg } = storeToRefs(
  music()
);

defineComponent({
  name: "MusicControls",
});
</script>

<template>
  <div class="music-controls">
    <div class="main">
      <div class="music-header">
        <ProgressLine :schedule="getCurrentSchedule" />
      </div>
      <div class="music-body">
        <div class="music-body__left">
          <Information
            :isPaused="getIsPaused"
            :isToggleImg="getIsToggleImg"
            :musicInfo="getMusicDescription"
          />
        </div>
        <div class="music-body__right">
          <!-- 控制音乐 -->
          <AudioControls />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.music-controls {
  box-sizing: border-box;
  background: transparent;
  display: flex;
  justify-content: center;
  .main {
    width: 1080px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .music-header {
    width: 100%;
  }
  .music-body {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 3px 3rem;
    &__left {
      width: 33%;
    }

    &__right {
      width: 68%;
    }
  }
}

.change-color:hover {
  cursor: pointer;
  color: #62c28a;
}

// mobile
@media screen and (max-width: 768px) {
  .main {
    width: 414px !important;
  }

  .music-body {
    padding: 3px 1rem !important;
    &__left {
      width: 30% !important;
    }

    &__right {
      width: 70% !important;
    }
  }
}
</style>
