<script>
import constants from "@/constants.js"
import { jwtDecode } from "jwt-decode"
import { toSignUpPage, toUserPage } from "@/utils.js"

export default {
  data() {
    return {
      signInData: {
        username: "",
        password: "",
        someOtherChanges: true,
      },
      errorOccured: false,
      passwordHidden: true,
      passwordFocused: false,
    }
  },
  methods: {
    toSignUpPage,
    async signIn() {
      const payload = {
        username: this.signInData.username,
        password: this.signInData.password,
      }
      const response = await this.$axios
        .post("/auths/login/", payload)
        .catch((error) => {
          console.log(error.toString())
          this.errorOccured = true
        })
      if ((await response).status === 200) {
        this.errorOccured = false
        localStorage.setItem(constants.accessToken, response.data.access)
        localStorage.setItem(constants.refreshToken, response.data.refresh)
        const userData = jwtDecode(localStorage.getItem(constants.accessToken))
        await toUserPage(userData.user_id)
        this.clearSignInData()
      } else {
        this.errorOccured = true
      }
    },
    clearSignInData() {
      this.signInData.password = ""
      this.signInData.username = ""
    },
  },
  name: "SignInPage",
}
</script>
<template>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"
    rel="stylesheet" />
  <div
    class="absolute top-0 -z-[101] h-full w-full animate-pulse bg-slate-950"></div>
  <img
    alt=""
    class="fixed top-0 -z-[100] h-full w-full object-cover blur-[2px] brightness-[80%]"
    src="@/assets/images/background-1.png" />
  <div class="h-full min-h-screen w-full pb-4 pt-2">
    <Container class="pt-[100px] sm:pt-[188px]">
      <div class="flex flex-col justify-center gap-8 md:flex-row">
        <div
          class="flex h-full w-full basis-1/2 animate-fade-up select-none flex-col gap-2.5 overflow-hidden rounded-xl bg-white px-4 pb-2 pt-2.5 text-center animate-delay-[300ms] animate-duration-[600ms] animate-once">
          <span class="text-[24px] font-bold">Вход</span>
          <form class="flex flex-col gap-2.5" method="post">
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]">Имя пользователя</label>
              <input
                v-model="signInData.username"
                class="w-full rounded-[0.3rem] border-[1px] border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                type="email" />
            </div>
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]">Пароль</label>
              <div class="flex flex-row">
                <input
                  v-if="passwordHidden"
                  v-model="signInData.password"
                  class="w-full rounded-l-[0.3rem] border-b border-l border-t border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                  placeholder="********"
                  type="password"
                  @focusin="passwordFocused = !passwordFocused"
                  @focusout="passwordFocused = !passwordFocused" />
                <input
                  v-else
                  v-model="signInData.password"
                  class="w-full rounded-l-[0.3rem] border-b border-l border-t border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                  placeholder="********"
                  type="text"
                  @focusin="passwordFocused = !passwordFocused"
                  @focusout="passwordFocused = !passwordFocused" />
                <div
                  :class="passwordFocused ? 'border-[#4285F4]' : ''"
                  class="flex aspect-square w-7 cursor-pointer items-center justify-center rounded-r-[0.3rem] border-b border-r border-t border-[#ADADAD] pr-1">
                  <i
                    :class="passwordHidden ? 'bi-eye' : 'bi-eye-slash'"
                    class="bi block text-black"
                    @click.prevent="passwordHidden = !passwordHidden"></i>
                </div>
              </div>
            </div>
            <span
              v-if="errorOccured"
              class="text-left text-[14px] text-red-600">
              Введённые аутентификационные данные неверны!
            </span>
            <button
              class="w-full rounded-[0.3rem] bg-[#4B7DDD] py-1.5 text-[14px] font-medium text-white transition-all duration-150 ease-in-out hover:drop-shadow-md active:bg-[#21B3E2] active:drop-shadow-none"
              type="submit"
              @click.prevent="signIn()">
              Войти
            </button>
            <span class="text-[14px]"
              >Впервые у нас?&nbsp;
              <span
                class="cursor-pointer text-[#E9583B] hover:underline"
                @click="toSignUpPage()"
                >Регистрация</span
              >
            </span>
          </form>
        </div>
        <div class="flex basis-1/2 select-none flex-col gap-3">
          <span class="text-[24px] font-medium text-white 2xl:text-[26px]"
            >С возвращением!</span
          >
          <p
            class="text-justify text-[16px] font-normal text-white 2xl:text-[18px]">
            <b class="text-[18px] font-bold 2xl:text-[20px]">E-Sayahat</b> — Ваш
            проводник в мир незабываемых путешествий. Мы специализируемся на
            создании уникальных туров по самым интересным и захватывающим
            направлениям по всему миру. Наша команда опытных профессионалов
            обеспечит вам высочайший уровень сервиса и индивидуальный подход к
            каждому клиенту.
          </p>
        </div>
      </div>
    </Container>
  </div>
</template>

<style></style>
