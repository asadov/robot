<template>
    <div>
        <div class="top-row">
            <div class="top part">
                <img v-bind:src="avaibleParts.heads[selectedHeadIndex].src" title="head"/>
                <button v-on:click="selectPreviousHead()" class="prev-selector">&#9668;</button>
                <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
            </div>
        </div>
        <div class="middle-row">
            <div class="left part">
                <img v-bind:src="avaibleParts.arms[selectedLeftArmIndex].src" title="left arm"/>
                <button v-on:click="selectPreviousLeftArm()" class="prev-selector">&#9650;</button>
                <button v-on:click="selectNextLeftArm()">&#9660;</button>
            </div>
            <div class="center part">
                <img v-bind:src="avaibleParts.torsos[selectedTorsosIndex].src" title="left arm"/>
                <button v-on:click="selectPreviousTorsos()" class="prev-selector">&#9668;</button>
                <button v-on:click="selectNextTorsos()" class="next-selector">&#9658;</button>
            </div>
            <div class="right part">
                <img v-bind:src="avaibleParts.arms[selectedRightArmIndex].src" title="left arm"/>
                <button v-on:click="selectPreviousRightArm()" class="prev-selector">&#9650;</button>
                <button v-on:click="selectNextRightArm()" class="next-selector">&#9660;</button>
            </div>
        </div>
        <div class="bottom-row">
            <div class="bottom part">
                <img v-bind:src="avaibleParts.bases[selectedBaseIndex].src" title="left arm"/>
                <button v-on:click="selectPreviousBase()" class="prev-selector">&#9668;</button>
                <button v-on:click="selectNextBase()" class="next-selector">&#9658;</button>
            </div>
        </div>
    </div>
</template>

<script>

import avaibleParts from '../data/parts.js';

function getPreviousValidIndex(index, length) {
  const deprecatedIndex = index - 1;
  return deprecatedIndex < 0 ? length - 1 : deprecatedIndex;
}

function getNextValidIndex(index, length) {
  const incrementedIndex = index + 1;
  return incrementedIndex > length - 1 ? 0 : incrementedIndex;
}

export default {
  name: 'RobotBuilder',
  data() {
    return {
      avaibleParts,
      selectedHeadIndex: 0,
      selectedLeftArmIndex: 0,
      selectedRightArmIndex: 0,
      selectedTorsosIndex: 0,
      selectedBaseIndex: 0,
    };
  },
  methods: {
    selectNextHead() {
      this.selectedHeadIndex = getNextValidIndex(this.selectedHeadIndex, avaibleParts.heads.length);
    },
    selectPreviousHead() {
      this.selectedHeadIndex = getPreviousValidIndex(this.selectedHeadIndex, avaibleParts.heads.length);
    },
    selectNextLeftArm() {
      this.selectedLeftArmIndex = getNextValidIndex(this.selectedLeftArmIndex, avaibleParts.arms.length);
    },
    selectPreviousLeftArm() {
      this.selectedLeftArmIndex = getNextValidIndex(this.selectedLeftArmIndex, avaibleParts.arms.length);
    },
    selectNextRightArm() {
      this.selectedRightArmIndex = getNextValidIndex(this.selectedRightArmIndex, avaibleParts.arms.length);
    },
    selectPreviousRightArm() {
      this.selectedRightArmIndex = getNextValidIndex(this.selectedRightArmIndex, avaibleParts.arms.length);
    },
    selectNextTorsos() {
      this.selectedTorsosIndex = getNextValidIndex(this.selectedTorsosIndex, avaibleParts.torsos.length);
    },
    selectPreviousTorsos() {
      this.selectedTorsosIndex = getNextValidIndex(this.selectedTorsosIndex, avaibleParts.torsos.length);
    },
    selectNextBase() {
      this.selectedBaseIndex = getNextValidIndex(this.selectedBaseIndex, avaibleParts.bases.length);
    },
    selectPreviousBase() {
      this.selectedBaseIndex = getNextValidIndex(this.selectedBaseIndex, avaibleParts.bases.length);
    },


  },
};

</script>

<style scoped>
    .part {
        position: relative;
        width:165px;
        height:165px;
        border: 3px solid #aaa;
    }
    .part img {
        width:165px;
    }
    .top-row {
        display:flex;
        justify-content: space-around;
    }
    .middle-row {
        display:flex;
        justify-content: center;
    }
    .bottom-row {
        display:flex;
        justify-content: space-around;
        border-top: none;
    }
    .head {
        border-bottom: none;
    }
    .left {
        border-right: none;
    }
    .right {
        border-left: none;
    }
    .left img {
        transform: rotate(-90deg);
    }
    .right img {
        transform: rotate(90deg);
    }
    .bottom {
        border-top: none;
    }
    .prev-selector {
        position: absolute;
        z-index:1;
        top: -3px;
        left: -28px;
        width: 25px;
        height: 171px;
    }
    .next-selector {
        position: absolute;
        z-index:1;
        top: -3px;
        right: -28px;
        width: 25px;
        height: 171px;
    }
    .center .prev-selector, .center .next-selector {
        opacity:0.8;
    }
    .left .prev-selector {
        top: -28px;
        left: -3px;
        width: 144px;
        height: 25px;
    }
    .left .next-selector {
        top: auto;
        bottom: -28px;
        left: -3px;
        width: 144px;
        height: 25px;
    }
    .right .prev-selector {
        top: -28px;
        left: 24px;
        width: 144px;
        height: 25px;
    }
    .right .next-selector {
        top: auto;
        bottom: -28px;
        left: 24px;
        width: 144px;
        height: 25px;
    }
    .right .next-selector {
        right: -3px;
    }
</style>
