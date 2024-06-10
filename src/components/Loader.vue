<script lang="ts" setup>

export type LoaderProps = {
  type?: string;
  primaryColor?: string;
  secondaryColor?: string;
  tertiaryColor?: string;
  position?: string;
};
const props = defineProps<LoaderProps>();

const {
  type = 'spinner',
  primaryColor = '#000000',
  secondaryColor = '#ffffff',
  tertiaryColor = '#ecf0f1',
  position = '',
} = props;

</script>

<template>
  <div
    class="loader-quark"
    :class="'loader-quark--' + props.type + ' ' + 'loader-quark--' + props.position"
  >
  </div>
</template>

<style>
.loader-quark {
  color: inherit;
  background-color: transparent;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* ------------------------------- POSITIONS ------------------------------- */
.loader-quark--top {
  position: absolute;
  top: 1rem;
  bottom: auto;
  left: 50%;
  transform: translateX(-50%);
  right: auto;
}
.loader-quark--top-right {
  position: absolute;
  top: 1rem;
  bottom: auto;
  right: 1rem;
  left: auto;
}
.loader-quark--top-left {
  position: absolute;
  top: 1rem;
  bottom: auto;
  left: 1rem;
  right: auto;
}
.loader-quark--bottom {
  position: absolute;
  bottom: 1rem;
  top: auto;
  left: 50%;
  transform: translateX(-50%);
  right: auto;
}
.loader-quark--bottom-right {
  position: absolute;
  bottom: 1rem;
  top: auto;
  right: 1rem;
  left: auto;
}
.loader-quark--bottom-left {
  position: absolute;
  bottom: 1rem;
  top: auto;
  left: 1rem;
  right: auto;
}
.loader-quark--left {
  position: absolute;
  left: 1rem;
  top: 50%;
  transform: translateY(-50%);
  right: auto;
}
.loader-quark--right {
  position: absolute;
  right: 1rem;
  top: 50%;
  transform: translateY(-50%);
  left: auto;
}



/* --------------------------------- TYPES --------------------------------- */
.loader-quark--spinner {
  width: 2rem;
  padding: 0.3rem;
  aspect-ratio: 1;
  border-radius: 50%;
  background: v-bind(primaryColor);
  --_m:
      conic-gradient(transparent 10%, v-bind(primaryColor)),
      linear-gradient(v-bind(primaryColor) 0 0) content-box;
  -webkit-mask: var(--_m);
  mask: var(--_m);
  -webkit-mask-composite: source-out;
  mask-composite: subtract;
  animation: spinner 1s infinite linear;
}

.loader-quark--spinner-1 {
  width: 2rem;
  aspect-ratio: 1;
  border-radius: 50%;
  background:
      radial-gradient(farthest-side,v-bind(primaryColor) 94%, transparent) top/0.4rem 0.4rem no-repeat,
      conic-gradient(transparent 30%,v-bind(primaryColor));
  -webkit-mask: radial-gradient(farthest-side,transparent calc(100% - 0.4rem),v-bind(primaryColor) 0);
  animation: spinner 1s infinite linear;
}

.loader-quark--spinner-2 {
  width: 2rem;
  aspect-ratio: 1;
  border-radius: 50%;
  border: 0.4rem solid;
  border-color: v-bind(primaryColor) transparent;
  animation: spinner2 1s infinite;
}

.loader-quark--spinner-3 {
  width: 2rem;
  aspect-ratio: 1;
  border-radius: 50%;
  border: 0.4rem solid v-bind(primaryColor);
  animation:
      spinner3-1 0.8s infinite linear alternate,
      spinner3-2 1.6s infinite linear;
}

.loader-quark--spinner-4 {
  width: 2rem;
  aspect-ratio: 1;
  display:grid;
  -webkit-mask: conic-gradient(from 15deg, transparent, v-bind(primaryColor));
  animation: spinner4 1s infinite steps(12);
}
.loader-quark--spinner-4,
.loader-quark--spinner-4:before,
.loader-quark--spinner-4:after{
  background:
      radial-gradient(closest-side at 50% 12.5%,
      v-bind(primaryColor) 96%, transparent) 50% 0/20% 80% repeat-y,
      radial-gradient(closest-side at 12.5% 50%,
      v-bind(primaryColor) 96%, transparent) 0 50%/80% 20% repeat-x;
}
.loader-quark--spinner-4:before,
.loader-quark--spinner-4:after {
  content: "";
  grid-area: 1/1;
  transform: rotate(30deg);
}
.loader-quark--spinner-4:after {
  transform: rotate(60deg);
}

.loader-quark--dots {
  width: 3rem;
  aspect-ratio: 4;
  --_g: no-repeat radial-gradient(circle closest-side, v-bind(primaryColor) 90%, transparent);
  background:
      var(--_g) 0%   50%,
      var(--_g) 50%  50%,
      var(--_g) 100% 50%;
  background-size: calc(100%/3) 100%;
  animation: dots 1s infinite linear;
}

/* HTML: <div class="loader"></div> */
.loader-quark--dots-2 {
  height: 1.5rem;
  aspect-ratio: 2.5;
  --_g: no-repeat radial-gradient(farthest-side,v-bind(primaryColor) 90%, transparent);
  background:var(--_g), var(--_g), var(--_g), var(--_g);
  background-size: 20% 50%;
  animation: dots2 1s infinite linear;
}

.loader-quark--line {
  width: 2rem;
  aspect-ratio: 1;
  --c:no-repeat linear-gradient(v-bind(primaryColor) 0 0);
  background:
      var(--c) 0 0,
      var(--c) 100% 0,
      var(--c) 100% 100%,
      var(--c) 0 100%;
  animation:
      line-1 2s infinite,
      line-2 2s infinite;
}


/* ------------------------------ ANIMATIONS ------------------------------ */
@keyframes spinner {
  to {transform: rotate(1turn)}
}
@keyframes spinner2 {
  to {transform: rotate(.5turn)}
}
@keyframes spinner3-1{
  0%    {clip-path: polygon(50% 50%,0       0,  50%   0%,  50%    0%, 50%    0%, 50%    0%, 50%    0% )}
  12.5% {clip-path: polygon(50% 50%,0       0,  50%   0%,  100%   0%, 100%   0%, 100%   0%, 100%   0% )}
  25%   {clip-path: polygon(50% 50%,0       0,  50%   0%,  100%   0%, 100% 100%, 100% 100%, 100% 100% )}
  50%   {clip-path: polygon(50% 50%,0       0,  50%   0%,  100%   0%, 100% 100%, 50%  100%, 0%   100% )}
  62.5% {clip-path: polygon(50% 50%,100%    0, 100%   0%,  100%   0%, 100% 100%, 50%  100%, 0%   100% )}
  75%   {clip-path: polygon(50% 50%,100% 100%, 100% 100%,  100% 100%, 100% 100%, 50%  100%, 0%   100% )}
  100%  {clip-path: polygon(50% 50%,50%  100%,  50% 100%,   50% 100%,  50% 100%, 50%  100%, 0%   100% )}
}
@keyframes spinner3-2{
  0%    {transform:scaleY(1)  rotate(0deg)}
  49.99%{transform:scaleY(1)  rotate(135deg)}
  50%   {transform:scaleY(-1) rotate(0deg)}
  100%  {transform:scaleY(-1) rotate(-135deg)}
}
@keyframes spinner4 {
  100% {transform:rotate(1turn)}
}
@keyframes dots {
  33%{background-size:calc(100%/3) 0%  ,calc(100%/3) 100%,calc(100%/3) 100%}
  50%{background-size:calc(100%/3) 100%,calc(100%/3) 0%  ,calc(100%/3) 100%}
  66%{background-size:calc(100%/3) 100%,calc(100%/3) 100%,calc(100%/3) 0%  }
}
@keyframes dots2 {
  0%     {background-position: calc(0*100%/3) 50% ,calc(1*100%/3) 50% ,calc(2*100%/3) 50% ,calc(3*100%/3) 50% }
  16.67% {background-position: calc(0*100%/3) 0   ,calc(1*100%/3) 50% ,calc(2*100%/3) 50% ,calc(3*100%/3) 50% }
  33.33% {background-position: calc(0*100%/3) 100%,calc(1*100%/3) 0   ,calc(2*100%/3) 50% ,calc(3*100%/3) 50% }
  50%    {background-position: calc(0*100%/3) 50% ,calc(1*100%/3) 100%,calc(2*100%/3) 0   ,calc(3*100%/3) 50% }
  66.67% {background-position: calc(0*100%/3) 50% ,calc(1*100%/3) 50% ,calc(2*100%/3) 100%,calc(3*100%/3) 0   }
  83.33% {background-position: calc(0*100%/3) 50% ,calc(1*100%/3) 50% ,calc(2*100%/3) 50% ,calc(3*100%/3) 100%}
  100%   {background-position: calc(0*100%/3) 50% ,calc(1*100%/3) 50% ,calc(2*100%/3) 50% ,calc(3*100%/3) 50% }
}
@keyframes line-1 {
  0%   {background-size: 0    4px,4px 0   ,0    4px,4px 0   }
  12.5%{background-size: 100% 4px,4px 0   ,0    4px,4px 0   }
  25%  {background-size: 100% 4px,4px 100%,0    4px,4px 0   }
  37.5%{background-size: 100% 4px,4px 100%,100% 4px,4px 0   }
  45%,
  55%  {background-size: 100% 4px,4px 100%,100% 4px,4px 100%}
  62.5%{background-size: 0    4px,4px 100%,100% 4px,4px 100%}
  75%  {background-size: 0    4px,4px 0   ,100% 4px,4px 100%}
  87.5%{background-size: 0    4px,4px 0   ,0    4px,4px 100%}
  100% {background-size: 0    4px,4px 0   ,0    4px,4px 0   }
}
@keyframes line-2 {
  0%,49.9%{background-position: 0 0   ,100% 0   ,100% 100%,0 100%}
  50%,100%{background-position: 100% 0,100% 100%,0    100%,0 0   }
}
</style>