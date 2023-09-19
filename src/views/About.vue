<template>
  <div class="about">
    <transition
      name="fade"
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
    >
      <!-- to check the leave hooks -->
      <h1 v-if="showTitle">About</h1>
    </transition>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const showTitle = ref(true);

    const beforeEnter = (el) => {
      console.log("Before", el);
    };
    const enter = (el) => {
      console.log("Enter", el);
    };
    const afterEnter = (el) => {
      el.style.color = "green";
      console.log("after", el);

      // to check leave hooks
      setTimeout(() => (showTitle.value = false), 2000);
    };
    const beforeLeave = (el) => {
      el.style.color = "Pink";
      console.log("Before leave", el);
    };
    const leave = (el) => {
      console.log("leave", el);
    };
    const afterLeave = (el) => {
      console.log("after leave", el);
    };

    return {
      beforeEnter,
      enter,
      afterEnter,
      showTitle,
      beforeLeave,
      leave,
      afterLeave,
    };
  },
};
</script>

<style>
.about {
  max-width: 600px;
  margin: 20px auto;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-to {
}
.fade-enter-active {
  transition: opacity 3s ease;
}
.fade-leave-from {
}
.fade-leave-to {
  opacity: 0;
}
.fade-leave-active {
  transition: opacity 3s ease;
}
</style>
