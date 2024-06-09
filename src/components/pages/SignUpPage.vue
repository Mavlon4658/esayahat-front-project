<script>
import {useStore} from "@/stores/store.js";
import { vMaska } from "maska";

export default {
  directives: { maska: vMaska },
  data() {
    return {
      store: useStore(),
      maskedValue: '',
      bindedObject: {
          masked: "",
          unmasked: "",
          completed: false,
      },
    };
  },
  name: "SignUpPage"
};
</script>
<template>
  <link href="https://fonts.googleapis.com/css2?family=Public+Sans:ital,wght@0,100..900;1,100..900&display=swap"
        rel="stylesheet">
  <img
    alt="background image"
    class="object-cover h-full w-full absolute top-0 -z-[100]"
    src="@/assets/images/background-1.png"
  />
  <Container>
    <div class="h-full w-full min-h-screen py-[100px] sm:pt-[188px] sm:pb-[133px]">
      <div class="flex flex-col-reverse sm:flex-row gap-8">
        <div class="w-full sm:w-60 rounded-lg px-4 pt-2.5 pb-2 gap-2 flex-col flex bg-white text-center">
          <span class="font-bold text-md">Регистрация</span>
          <form class="flex flex-col gap-2" method="post">

            <label class="text-[12px] text-start">Ф.И.О.</label>
            <input
              class="w-full text-[14px] rounded-[0.3rem] ring-[#ADADAD] ring-[1px] px-2 py-1.5 focus:ring-[#4285F4]"
              placeholder="Введите свои имя, фамилию и отчество"
              type="text"
              autofocus
            >

            <label class="text-[12px] text-start">Номер телефона</label>
            <input
              v-model="maskedValue"
              v-maska="bindedObject"
              data-maska="+7 (###) ### ## ##"
              placeholder="+7 ..."
              class="w-full text-[14px] rounded-[0.3rem] ring-[#ADADAD] ring-[1px] px-2 py-1.5"
            >

            <label class="text-[12px] text-start">Почта</label>
            <input
              type="email"
              placeholder="user@mail.ru"
              class="w-full text-[14px] rounded-[0.3rem] ring-[#ADADAD] ring-[1px] px-2 py-1.5"
            >

            <label class="text-[12px] text-start">Придумайте пароль</label>
            <input
              type="password"
              placeholder="user@mail.ru"
              class="w-full text-[14px] rounded-[0.3rem] ring-[#ADADAD] ring-[1px] px-2 py-1.5"
            >

            <label class="text-[12px] text-start">Повторите пароль</label>
            <input
              type="password"
              placeholder="user@mail.ru"
              class="w-full text-[14px] rounded-[0.3rem] ring-[#ADADAD] ring-[1px] px-2 py-1.5"
            >

            <button class="bg-[#4B7DDD] w-full py-2 text-white rounded-md text-[12px] drop-shadow-md mt-[20px]" type="submit"
                    @submit.prevent="">Создать аккаунт
            </button>

            <span class="text-[12px]">У вас уже есть аккаунт? &nbsp;
            <span class="text-[#E9583B] cursor-pointer" @click="$router.push('/sign-in')">Войти</span>
          </span>
          </form>
        </div>
        <div class="flex flex-col gap-4 text-center sm:text-left">
          <span class="font-medium text-[33px] text-white">Добро пожаловать!</span>
          <p class="font-normal text-[14px] text-white">STUAIR – Ваш проводник в мир незабываемых путешествий. Мы
            <br class="hidden sm:block">специализируемся на создании уникальных туров по самым интересным<br class="hidden sm:block">и захватывающим направлениям по всему
            миру. <br class="block sm:hidden">
            Наша команда опытных
            <br class="hidden sm:block">
            профессионалов обеспечит вам высочайший уровень сервиса и
            <br class="hidden sm:block">индивидуальный подход к каждому клиенту.</p>
        </div>
      </div>
    </div>
  </Container>
</template>

<style></style>
