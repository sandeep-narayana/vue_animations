<template>
  <div class="about">
    <transition
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
    >
      <!-- to check the leave hooks -->
      <h1>About - 2</h1>
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
import gsap from "gsap";
export default {
  setup() {
    // bounce effect
    const beforeEnter = (el) => {
      console.log("before enter - set initial state");
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };

    // second argumnet to tell view that the enter animation is finished otherwise it will trigger the after Enter
    const enter = (el, done) => {
      //   use g sap otherwise animation will not work
      console.log("starting to enter - make transition");
      gsap.to(el, {
        duration: 3,
        y: 0,
        opacity: 1,
        ease: "bounce.out",
        onComplete: done,
      });
    };

    //
    const afterEnter = () => {
      console.log("after enter");
    };

    return {
      beforeEnter,
      enter,
      afterEnter,
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
