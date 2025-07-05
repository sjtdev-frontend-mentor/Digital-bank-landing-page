<template>
  <div class="header bg-very-light-gray relative mt-[64px] flex flex-none flex-col overflow-hidden lg:mt-[80px] lg:items-start lg:overflow-x-hidden">
    <div class="relative mx-auto max-w-[1100px]  bg-[url('/images/bg-intro-mobile.svg')] bg-position-[0px_-55px] bg-no-repeat lg:bg-[url('/images/bg-intro-desktop.svg')] lg:bg-[position:calc(100%_-_-450px)_-264px]">
      <div class="absolute h-screen right-0 w-full overflow-hidden">
        <img class="absolute top-[-124px] z-0 px-[12px] lg:right-[-142px]" src="/images/image-mockups.png" alt="" /></div>
      <section class="mt-[323px] flex flex-col items-center justify-center gap-[16px] px-[24px] pb-[88px] text-center lg:mx-auto lg:mt-0 lg:h-[656px] lg:w-[1100px] lg:items-start lg:gap-[20px] lg:p-0 lg:text-left">
        <h1 class="text-dark-blue text-[38px] leading-[47px] lg:w-[400px] lg:text-[40px]">Next generation digital banking</h1>
        <p class="text-grayish-blue mb-[12px] text-[14.5px] leading-[26px] lg:w-[400px] lg:text-[16px]">
          Take your financial life online. Your Easybank account will be a one-stop-shop for spending, saving, budgeting, investing, and much more.
        </p>
        <RequestInviteButton />
      </section>
    </div>

    <section class="bg-light-grayish-blue flex w-full flex-col items-center gap-[36px] px-[28px] py-[70px] text-center lg:w-full lg:items-start lg:p-0 lg:py-[100px] lg:text-left">
      <div class="mb-[24px] flex flex-col gap-[24px] lg:mx-auto lg:w-[1100px]">
        <h2 class="text-dark-blue text-3xl">Why choose Easybank?</h2>
        <p class="text-grayish-blue text-base lg:w-[600px]">We leverage Open Banking to turn your bank account into your financial hub. Control your finances like never before.</p>
      </div>
      <div class="flex flex-col gap-[32px] lg:mx-auto lg:w-[1100px] lg:flex-row">
        <div v-for="choose in choosen" class="flex flex-col items-center gap-[24px] lg:items-start">
          <img :src="choose.icon" alt="" />
          <h3 class="text-dark-blue text-xl">{{ choose.title }}</h3>
          <p class="text-grayish-blue text-sm">{{ choose.description }}</p>
        </div>
      </div>
    </section>
  </div>
  <article class="bg-very-light-gray w-full">
    <section class="flex flex-col items-center gap-[24px] px-[24px] pt-[96px] pb-[88px] lg:mx-auto lg:w-[1100px] lg:items-start lg:p-0 lg:py-[100px]">
      <h2 class="text-dark-blue pb-[12px] text-3xl">Latest Articles</h2>
      <div class="flex flex-col gap-[24px] lg:flex-row">
        <div v-for="article in articles">
          <img class="h-[200px] w-[327px] object-cover" :src="article.image" alt="" />
          <div class="flex h-[195px] flex-col gap-[16px] bg-white px-[32px] pt-[30px] pb-[46px] lg:gap-[10px]">
            <h4 class="text-grayish-blue text-[9.7px]">By {{ article.author }}</h4>
            <a class="text-dark-blue hover:text-lime-green text-[15.5px] leading-[20px]" href="#">{{ article.title }}</a>
            <p class="text-grayish-blue text-[12.5px] lg:text-[11.8px]">{{ article.description }}</p>
          </div>
        </div>
      </div>
    </section>
  </article>
</template>

<script setup lang="ts">
import RequestInviteButton from "./RequestInviteButton.vue";

const baseURL = import.meta.env.BASE_URL;

type Choosen = {
  title: string;
  description: string;
  icon: string;
};
type Article = {
  title: string;
  description: string;
  author: string;
  image: string;
};

const choosen: Choosen[] = [
  {
    title: "Online Banking",
    description: "Our modern web and mobile applications allow you to keep track of your finances wherever you are in the world.",
    icon: "images/icon-online.svg",
  },
  {
    title: "Simple Budgeting",
    description: "See exactly where your money goes each month. Receive notifications when you’re close to hitting your limits.",
    icon: "images/icon-budgeting.svg",
  },
  {
    title: "Fast Onboarding",
    description: "We don’t do branches. Open your account in minutes online and start taking control of your finances right away.",
    icon: "images/icon-onboarding.svg",
  },
  {
    title: "Open API",
    description: "Manage your savings, investments, pension, and much more from one account. Tracking your money has never been easier.",
    icon: "images/icon-api.svg",
  },
];

const articles: Article[] = [
  {
    title: "Receive money in any currency with no fees",
    description: "The world is getting smaller and we’re becoming more mobile. So why should you be forced to only receive money in a single …",
    author: "Claire Robinson",
    image: "images/image-currency.jpg",
  },
  {
    title: "Treat yourself without worrying about money",
    description: "Our simple budgeting feature allows you to separate out your spending and set realistic limits each month. That means you …",
    author: "Wilson Hutton",
    image: "images/image-restaurant.jpg",
  },
  {
    title: "Take your Easybank card wherever you go",
    description: "We want you to enjoy your travels. This is why we don’t charge any fees on purchases while you’re abroad. We’ll even show you …",
    author: "Wilson Hutton",
    image: "images/image-plane.jpg",
  },
  {
    title: "Our invite-only Beta accounts are now live!",
    description: "After a lot of hard work by the whole team, we’re excited to launch our closed beta. It’s easy to request an invite through the site.",
    author: "Claire Robinson",
    image: "images/image-confetti.jpg",
  },
];
</script>

<style scoped>
.background-header {
  background-image: var(--mobile-bg);
}
@media (min-width: 1024px) {
  .background-header {
    background-image: var(--desktop-bg);
  }
}
</style>
