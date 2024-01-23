<template>
    <main class="animation-wrapper">
        <div class="nav-bar flex justify-between w-[100%]">
            <i class='bx bx-menu-alt-left text-[24px] ml-[-3rem] menu'></i>
            <i class='bx bxs-user-circle text-[24px] mr-[-3rem] profile'></i>
        </div>
        <img class="absolute h-[200px] left-[50%] top-[20%] car car-1" src="../assets/car-front.png">
        <div>
            <h1 class="text-xl absolute bottom-[-32%] left-[50%] text-center text-[#313942] heading">Model S</h1>
            <p class="w-[260px] copy font-medium text-[14px] absolute bottom-[-18%] left-[50%] text-center text-[#535c68]">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam.</p>
            <div class="buy" @click="playAnimation">
                <i class='bx bxs-cart-alt'></i>
            </div>
        </div>
        <img class="car-2 absolute h-[100px] left-[200%] top-[10%]" src="../assets/car-side.png">
        <h2 class="congrats-title absolute top-[38%] left-[-60%] text-white w-[100%]">Congratulations!</h2>
        <h5 class="summary absolute top-[46%] left-[-52%] text-white w-[83%] font-medium opacity-[0.8]">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt.
        </h5>
        <h5 class="summary-2 absolute top-[58%] left-[-52%] text-white w-[83%] font-medium opacity-[0.8]">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt.
        </h5>
        <i @click="reverseAnimation" class='bx bx-arrow-back back-button p-4 text-[24px] text-[silver] absolute left-[35px] bottom-[-25%]'></i>
    </main>
</template>
<script setup>
    import { onMounted } from 'vue';
    import gsap from 'gsap';

    const createTimeline = (paused = true, reversed = true) => gsap.timeline({ paused, reversed });
   /*  Timeline on mounted */
    const t1 = createTimeline();
    /*  Timeline on click */
    const t2 = createTimeline();
    /*  When basket is clicked */
    const playAnimation = () => t2.play();
    /*  Reverse Timeline when arrow is clicked */
    const reverseAnimation = () => t2.reverse();

    onMounted(() => {
    /*  Timeline 1 on mounted */
    t1.play();

    t1.to(".car-1", { ease: "elastic.out(1, .8)", top: "17%", duration: 1.5 });
    t1.to(".menu", { ease: "elastic.out(1, .8)", marginLeft: '1rem', duration: 1.5 }, 0.3);
    t1.to(".profile", { ease: "elastic.out(1, .8)", marginRight: '1rem', duration: 1.5 }, 0.3);
    t1.to(".heading", { ease: "elastic.out(1, .8)", bottom: "32%", duration: 1.5 }, 0.3);
    t1.to(".copy", { ease: "elastic.out(1, .8)", bottom: "13%", duration: 1.5 }, 0.4);
    t1.from(".buy", { ease: "elastic.out(1, .8)", scale: 0, duration: 1.5 }, 0.6);
    /*  Timeline 2 on click events */
    t2.to(".car-1", { ease: "elastic.out(1, .8)", top: "110%", duration: 2 });
    t2.to(".menu", { ease: "power1.inOut", left: -30 }, 0);
    t2.to(".profile", { ease: "power1.inOut", right: -30 }, 0);
    t2.to(".heading", { ease: "elastic.out(.5, .8)", bottom: "-32%" }, 0);
    t2.to(".copy", { ease: "elastic.out(1, .8)", bottom: "-18%" }, 0);
    t2.to(".buy i", { ease: "power1.inOut", scale: 0, duration: 0.3 }, 0);
    t2.to(".buy", { ease: "power1.inOut", scaleY: 16, width: '100%', borderRadius: 0, duration: 0.3 }, 0.3);
    t2.to(".back-button", { ease: "elastic.out(1, .8)", bottom: "5%", duration: 1.5 }, 0.7);
    t2.to(".car-2", { ease: "elastic.out(1, .8)", left: "50%", duration: 1.5 }, 0.5);
    t2.to(".congrats-title", { ease: "elastic.out(1, .8)", left: "60%", duration: 1.5 }, 0.5);
    t2.to(".summary", { ease: "elastic.out(1, .8)", left: "52%", duration: 1.5 }, 0.6);
    t2.to(".summary-2", { ease: "elastic.out(1, .8)", left: "52%", duration: 1.5 }, 0.7);
    });
</script>

<style>
        *,
    *::after,
    *::before {
        margin: 0;
        padding: 0;
        -webkit-box-sizing: inherit;
        box-sizing: inherit;
    }
    body {
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
        font-family: "Poppins", sans-serif;
        line-height: 1.7;
        position: relative;
        background-color: #ecf1f5;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .animation-wrapper {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        overflow: hidden;
        background-color: white;
        width: 320px;
        height: 680px;
        border-radius: 28px;
        box-shadow: 0px 56px 72px -30px rgba(50, 55, 63, 0.46);
        padding: 20px;
    }
    img {
    max-width: unset;
    }

    .car {
        transform: translate(-50%) !important;
    }

    h1,
    p  {
        transform: translate(-50%);
    }

    .buy {
        background-color: black;
        width: 50px;
        height: 50px;
        border-radius: 100%;
        position: absolute;
        bottom: 25px;
        left: 50%;
        transform: translate(-50%);
    }

    .buy i {
        font-size: 24px;
        color: white;
        display: flex;
        height: 100%;
        align-items: center;
        justify-content: center;
    }

    .car-2,
    .summary,
    .summary-2 {
        transform: translate(-50%);
    }

    .congrats-title {
        transform: translate(-50%);
    }
</style>