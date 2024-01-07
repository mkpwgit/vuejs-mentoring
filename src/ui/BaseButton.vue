<script setup>
import { defineProps } from 'vue'

defineProps(
    {mode: String, prependIcon: String, appendIcon: String, disabledBtn: Boolean, rounded: Boolean});

function svgColor(mode) {
  switch (mode) {
    case 'filled':
      return 'white';
    case 'outline':
    case 'text':
    case 'elevated':
      return '#6750A4';
    case 'tonal':
      return '#1D192B'
  }
}

function svgDisabledColor(mode) {
  switch (mode) {
    case 'filled':
    case 'outline':
    case 'text':
    case 'elevated':
      return '#1D1B20';
    case 'tonal':
      return '#1D192B'
  }
}

function svgIcon(name) {
  switch (name) {
    case 'add':
      return 'M15 9.75H9.75V15H8.25V9.75H3V8.25H8.25V3H9.75V8.25H15V9.75Z';
    case 'attach':
      return 'M13 14c0 2.21-1.79 4-4 4s-4-1.79-4-4V3c0-1.66 1.34-3 3-3s3 1.34 3 3v9c0 1.1-.9 2-2 2s-2-.9-2-2V4h1v8c0 .55.45 1 1 1s1-.45 1-1V3c0-1.1-.9-2-2-2s-2 .9-2 2v11c0 1.66 1.34 3 3 3s3-1.34 3-3V4h1v10z';
    case 'edit':
      return 'M2 12.88V16h3.12L14 7.12 10.88 4 2 12.88zm14.76-8.51c.33-.33.33-.85 0-1.18l-1.95-1.95c-.33-.33-.85-.33-1.18 0L12 2.88 15.12 6l1.64-1.63z';
    case 'back':
      return 'M15 8.25H5.87l4.19-4.19L9 3 3 9l6 6 1.06-1.06-4.19-4.19H15v-1.5z';
    case 'forward':
      return 'M9 3L7.94 4.06l4.19 4.19H3v1.5h9.13l-4.19 4.19L9 15l6-6z';
    default:
      return 'M15 9.75H9.75V15H8.25V9.75H3V8.25H8.25V3H9.75V8.25H15V9.75Z';
  }
}</script>
<template>
  <button :class="[mode, rounded ? 'rounded' : null]" v-if="!disabledBtn">
    <span>
      <svg v-if="prependIcon"
           xmlns="http://www.w3.org/2000/svg"
           width="18" height="18"
           viewBox="0 0 18 18"
           fill="none" class="prepend">
      <path :d="svgIcon(prependIcon)" :fill="svgColor(mode)"/>
      </svg>
      <slot></slot>
      <svg v-if="appendIcon"
           xmlns="http://www.w3.org/2000/svg"
           width="18"
           height="18"
           viewBox="0 0 18 18"
           fill="none"
           class="append">
        <path :d="svgIcon(prependIcon)" :fill="svgColor(mode)"/>
      </svg>
    </span>
  </button>
  <button :class="[mode + '-disabled', rounded ? 'rounded' : null]" disabled v-else>
    <span>
      <svg v-if="prependIcon"
           xmlns="http://www.w3.org/2000/svg"
           width="18"
           height="18"
           viewBox="0 0 18 18"
           fill="none"
           class="prepend">
        <g opacity="0.38">
          <path :d="svgIcon(prependIcon)"
                :fill="svgDisabledColor(mode)"/>
        </g>
      </svg>
      <slot></slot>
      <svg v-if="appendIcon"
           xmlns="http://www.w3.org/2000/svg"
           width="18"
           height="18"
           viewBox="0 0 18 18"
           fill="none"
           class="append">
        <g opacity="0.38">
          <path :d="svgIcon(appendIcon)" :fill="svgDisabledColor(mode)"/>
        </g>
      </svg>
    </span>
  </button>
</template>

<style scoped>

button {
  padding: 10px 24px 10px 24px;
  display: inline-block;
  height: 40px;
  cursor: pointer;
  margin-right: 15px;
  transition-duration: 0.2s;
  text-align: center;
  font-size: 14px;
  font-style: normal;
  font-weight: 500;
  line-height: 20px; /* 142.857% */
  letter-spacing: 0.1px;
}

.rounded {
  border-radius: 100px;
}

svg.prepend {
  margin-right: 8px;
}

svg.append {
  margin-left: 8px;
}

span {
  display: flex;
  text-align: center;
}

.filled {
  background-color: #6750A4;
  border: 1px solid #CAC4D0;
  color: #FFFFFF;
}

.filled:hover {
  opacity: 0.92;
  box-shadow: 0 0 3px 1px #00000026, 0 1px 2px 0 #0000004D;
}

.filled:active {
  opacity: 0.74;
  box-shadow: 0 0 3px 1px #00000026, 0 1px 2px 0 #0000004D;
}

.filled-disabled {
  background-color: #1D1B201F;
  color: #1D1B20;
}

.outline {
  background-color: transparent;
  border: 1px solid #79747E;
  color: #6750A4;
}

.outline:hover {
  background-color: #6750A414;
}

.outline:active {
  background-color: #6750A433;
}

.outline-disabled {
  border: 1px solid rgba(29, 27, 32, 0.12);
}

.text {
  background-color: transparent;
  border: 1px solid white;
  color: #6750A4;
}

.text:hover {
  background-color: #6750A414;
}

.text:active {
  background-color: #6750A433;
}

.text-disabled {
  background-color: transparent;
  border: 1px solid white;
}

.elevated {
  border: none;
  background-color: #F7F2FA;
  color: #6750A4;
  box-shadow: 0px 1px 3px 1px #00000026, 0px 1px 2px 0px #0000004C;
}

.elevated:hover {
  background-color: #FFFFFF1F; /* M3/Elevation Light/2 */
  box-shadow: 0px 2px 6px 2px #00000026, 0px 1px 2px 0px #0000004C;
}

.elevated:active {
  background: #F7F2FA; /* M3/Elevation Light/1 */
  box-shadow: 0px 1px 3px 1px #00000026, 0px 1px 2px 0px #0000004C;
}

.elevated-disabled {
  background-color: #1D1B201F;
  color: #1D1B20;
  opacity: 0.38;
}

.tonal {
  border: none;
  background: #E8DEF8;
  color: #1D192B;
}

.tonal:hover {
  opacity: 0.92;
  background: #E8DEF8;
  box-shadow: 0px 1px 3px 1px #00000026, 0px 1px 2px 0px #0000004C;
}

.tonal:active {
  opacity: 0.88;
  background: #E8DEF8;
  box-shadow: 0px 0px 0px 0px #00000026, 0px 0px 0px 0px #0000004C;
}

.tonal-disabled {
  background-color: #1D1B201F;
  color: #1D1B20;
  opacity: 0.38;
}

</style>
