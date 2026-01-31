<template>
  <div :class="classes">
    <AppLink is-external to="https://github.com/avinashsaxena777" aria-label="My Github" title="My Github">
      <svg width="30" height="30" viewBox="0 0 44 44" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M21.9805 0.725586C9.90527 0.720703 0.125 10.4961 0.125 22.5615C0.125 32.1025 6.24316 40.2129 14.7637 43.1914C15.9111 43.4795 15.7354 42.6641 15.7354 42.1074V38.3232C9.10938 39.0996 8.84082 34.7148 8.39648 33.9824C7.49805 32.4492 5.37402 32.0586 6.00879 31.3262C7.51758 30.5498 9.05566 31.5215 10.8379 34.1533C12.127 36.0625 14.6416 35.7402 15.916 35.4229C16.1943 34.2754 16.79 33.25 17.6104 32.4541C10.7451 31.2236 7.88379 27.0342 7.88379 22.0537C7.88379 19.6367 8.67969 17.415 10.2422 15.623C9.24609 12.6689 10.335 10.1396 10.4814 9.76367C13.3184 9.50977 16.2676 11.7949 16.4971 11.9756C18.1084 11.541 19.9492 11.3115 22.0098 11.3115C24.0801 11.3115 25.9258 11.5508 27.5518 11.9902C28.1035 11.5703 30.8379 9.60742 33.4746 9.84668C33.6162 10.2227 34.6807 12.6934 33.7432 15.6084C35.3252 17.4053 36.1309 19.6465 36.1309 22.0684C36.1309 27.0586 33.25 31.2529 26.3652 32.4639C26.9549 33.0438 27.4232 33.7354 27.7426 34.4983C28.062 35.2612 28.2262 36.0801 28.2256 36.9072V42.4004C28.2646 42.8398 28.2256 43.2744 28.958 43.2744C37.6055 40.3594 43.8311 32.1904 43.8311 22.5664C43.8311 10.4961 34.0459 0.725586 21.9805 0.725586Z"
          fill="#F4F4F4" />
      </svg>
    </AppLink>
    <AppLink
is-external to="https://www.linkedin.com/in/avinashsaxenaofficial/" aria-label="My LinkedIn Account"
      title="My LinkedIn">
      <svg width="30" height="30" viewBox="0 0 41 41" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M38.8281 0.578125H2.17188C1.29033 0.578125 0.578125 1.29033 0.578125 2.17188V38.8281C0.578125 39.7097 1.29033 40.4219 2.17188 40.4219H38.8281C39.7097 40.4219 40.4219 39.7097 40.4219 38.8281V2.17188C40.4219 1.29033 39.7097 0.578125 38.8281 0.578125ZM12.3968 34.53H6.48496V15.5146H12.3968V34.53ZM9.44336 12.9147C8.76565 12.9147 8.10316 12.7138 7.53966 12.3373C6.97617 11.9608 6.53698 11.4256 6.27763 10.7995C6.01828 10.1733 5.95042 9.48438 6.08264 8.81969C6.21485 8.15501 6.5412 7.54445 7.02041 7.06524C7.49963 6.58602 8.11018 6.25968 8.77487 6.12746C9.43956 5.99525 10.1285 6.0631 10.7546 6.32245C11.3808 6.5818 11.9159 7.02099 12.2924 7.58449C12.669 8.14798 12.8699 8.81047 12.8699 9.48818C12.8649 11.3808 11.331 12.9147 9.44336 12.9147ZM34.53 34.53H28.6231V25.2812C28.6231 23.0749 28.5833 20.241 25.5502 20.241C22.4772 20.241 22.0041 22.6416 22.0041 25.1219V34.53H16.1022V15.5146H21.77V18.1144H21.8497C22.6366 16.6202 24.5641 15.0414 27.4428 15.0414C33.4293 15.0414 34.53 18.981 34.53 24.1009V34.53Z"
          fill="#F4F4F4" />
      </svg>
    </AppLink>
    <AppLink
is-external to="mailto:avinashsaxenagrad@gmail.com" aria-label="Send me an email"
      title="Email Me">
      <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
         <path d="M22 6C22 4.9 21.1 4 20 4H4C2.9 4 2 4.9 2 6V18C2 19.1 2.9 20 4 20H20C21.1 20 22 19.1 22 18V6ZM20 6L12 11L4 6H20ZM20 18H4V8L12 13L20 8V18Z" fill="#F4F4F4"/>
      </svg>
    </AppLink>
    <AppLink
is-external to="https://leetcode.com/u/avinashs1995/" aria-label="My Leetcode profile"
      title="My Leetcode">
      <!-- Simple LeetCode Icon -->
      <img :src="leetcodeImg" alt="LeetCode" class="social-icon-img" />
    </AppLink>
    <AppLink
      is-external :to="resumePdf"
      variant="button"
      class="resume-btn"
      aria-label="View Resume"
      title="View Resume"
    >
      <span class="btn-content">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
          <path d="M5 20H19V18H5V20ZM19 9H15V3H9V9H5L12 16L19 9Z" />
        </svg>
        <span>View Resume</span>
      </span>
    </AppLink>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import leetcodeImg from '@/assets/img/leetcode.png'
const resumePdf = 'https://drive.google.com/file/d/1tcsaKL8sbcMqgNgCI9Z1HTrtuMSjj9QA/view?usp=sharing'

const props = defineProps({
  boxed: {
    type: Boolean,
    default: false,
  },
})

const classes = computed(() => ({
  'social-media-icons': true,
  'social-media-icons--boxed': props.boxed,
}))
</script>

<style scoped>
.social-media-icons {
  display: flex;
  align-items: center;

  & a {
    border-radius: var(--radius-default);
    padding: 0.25rem 0.5rem;
    outline: 0;

    &:hover,
    &:focus {
      transform: translateY(-4px);
    }

    &:hover svg,
    &:focus svg,
    &:hover svg path,
    &:focus svg path {
      fill: var(--color-primary);
    }
  }

  & a+a {
    margin-inline-start: 20px;
  }

  svg,
  .social-icon-img {
    max-width: 30px;
    max-height: 30px;
    object-fit: contain;
  }

  & :is(a, svg, path) {
    transition-duration: 400ms;
    transition-timing-function: cubic-bezier(0.22, 0.61, 0.36, 1);
    transition-property: transform, fill, box-shadow;
    will-change: transform;
  }
}

.resume-btn {
  /* Override AppLink button variables with custom theme color */
  --button-bg-color: rgb(231, 131, 54);
  --button-text-color: #ffffff;

  /* Ensure button styling takes precedence and looks good */
  display: inline-flex !important;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  
  /* Force colors to ensure readability in both themes */
  background-color: var(--button-bg-color) !important;
  color: var(--button-text-color) !important;
  border: 1px solid transparent; 
  
  .btn-content {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-weight: 600;
    /* Ensure text readability */
    text-shadow: 0 1px 2px rgba(0,0,0,0.1);
  }

  svg {
    width: 20px;
    height: 20px;
  }
  
  /* Force Icon color to match text color (white), overriding default theme hacks */
  & svg, 
  & svg path {
      fill: var(--button-text-color) !important;
  }
}

/* Override hover behavior to ensure icon stays white */
.social-media-icons .resume-btn:hover svg,
.social-media-icons .resume-btn:hover svg path {
  fill: var(--button-text-color) !important;
}

body[data-theme='light'] {
  .social-media-icons a:not(.resume-btn) {

    svg,
    svg path {
      fill: var(--color-default-black);
    }
  }
}

.social-media-icons--boxed {
  a {
    display: inline-block;
  }
}

@media (--vw-sm) {
  .social-media-icons {
    justify-content: center;
  }
}
</style>
