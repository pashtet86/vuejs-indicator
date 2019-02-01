<template>
  <span class="indicator" :class="statusClass">
    <i :style="circleStyle" />
    <div class="indicator__text" v-if="showtext" v-text="status" />
    <div
      v-else
      class="indicator__tooltip"
      :style="tooltipStyle"
      v-text="status"
    />
  </span>
</template>

<script>
export default {
  name: "indicator",
  props: {
    showtext: {
      type: Boolean,
      default: false
    },
    status: {
      type: String,
      default: ""
    },
    size: {
      type: Number,
      default: 8
    },
    backgroundColor: {
      type: String,
      default: "#333"
    }
  },
  computed: {
    statusClass() {
      return `indicator--${this.status.toLowerCase()}`;
    },
    tooltipStyle() {
      return { left: `${this.size / 2 - 15}px`, bottom: `${this.size}px` };
    },
    circleStyle() {
      return { width: `${this.size}px`, height: `${this.size}px` };
    }
  }
};
</script>

<style lang="scss">
$yellow: #ffa601;
$grey: #d1d1d1;
$green: #27b866;
$red: #f74e17;
$tooltipBg: #333;

.indicator {
  display: inline-flex;
  align-self: centre;
  vertical-laign: middle;
  align-items: center;
  justify-content: flex-start;
  margin-right: 10px;
  position: relative;
  cursor: pointer;

  i {
    flex-shrink: 0;
    display: block;
    width: 8px;
    height: 8px;
    flex-grow: 0;
    border-radius: 50%;
  }

  &__text {
    font-size: 18px;
    margin-left: 10px;
    text-transform: capitalize;
  }

  &__wrapper {
    display: flex;
    align-items: center;
    overflow: visible;
  }

  &__tooltip {
    font-size: 13px;
    line-height: 1.33;
    text-transform: capitalize;
    visibility: hidden;
    position: absolute;
    bottom: 0;
    margin-bottom: 10px;
    left: -10px;
    background-color: $tooltipBg;
    padding: 6px 12px;
    border-radius: 3px;
    opacity: 0;
    line-height: 1;
    font-weight: 300;
    color: white;
    transition: opacity 0.2s;

    &:after {
      content: "";
      position: absolute;
      width: 0;
      height: 0;
      border: 5px solid white;
      border-color: transparent $tooltipBg $tooltipBg transparent;
      box-sizing: border-box;
      transform-origin: 0 0;
      z-index: 3;
      left: 15px;
      bottom: 0;
      transform: rotate(45deg);
    }
  }

  &:hover .indicator__tooltip {
    visibility: visible;
    opacity: 0.9;
  }

  // coloring

  &--green,
  &--opened,
  &--active,
  &--current {
    i {
      background-color: $green;
    }
  }

  &--yellow,
  &--pending,
  &--draft,
  &--upcoming {
    i {
      background-color: $yellow;
    }
  }

  &--grey,
  &--inactive,
  &--finished,
  &--past {
    i {
      background-color: $grey;
    }
  }

  &--red,
  &--depricated,
  &--deleted {
    i {
      background-color: $red;
    }
  }
}
</style>
