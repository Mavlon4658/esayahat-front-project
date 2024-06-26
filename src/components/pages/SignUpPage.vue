<script>
import useVuelidate from "@vuelidate/core"
import {
  email,
  helpers,
  maxLength,
  minLength,
  required,
  sameAs,
} from "@vuelidate/validators"
import { toSignInPage } from "@/utils.js"
import constants from "@/constants.js"

export default {
  name: "SignUpPage",
  data() {
    return {
      signUpData: {
        username: "",
        email: "",
        firstname: "",
        lastname: "",
        password: "",
        passwordConfirm: "",
      },
      v$: useVuelidate(),
      password1Hidden: true,
      password1Focused: false,
      password2Hidden: true,
      password2Focused: false,
    }
  },
  methods: {
    toSignInPage,
    async signUp() {
      // await this.v$.$validate()
      if (this.v$.$errors.length <= 0 && this.v$.$anyDirty) {
        this.v$.$reset()
        const payload = {
          username: this.signUpData.username,
          first_name: this.signUpData.firstname,
          last_name: this.signUpData.lastname,
          email: this.signUpData.email,
          password: this.signUpData.password,
          password2: this.signUpData.passwordConfirm,
        }
        localStorage.setItem(constants.accessToken, null)
        localStorage.setItem(constants.refreshToken, null)
        const response = await this.$axios
          .post("/auths/users/", payload)
          .catch((error) => {
            console.log(error.toString())
          })
        if (
          (await response).status === 201 ||
          (await response).status === 200
        ) {
          await toSignInPage()
          this.clearSignUpData()
        }
      }
    },
    clearSignUpData() {
      this.signUpData.username = ""
      this.signUpData.email = ""
      this.signUpData.firstname = ""
      this.signUpData.lastname = ""
      this.signUpData.password = ""
      this.signUpData.passwordConfirm = ""
    },
  },
  validations() {
    return {
      signUpData: {
        username: {
          required: helpers.withMessage("Введите имя пользователя.", required),
          maxLength: helpers.withMessage(
            "Имя пользователя должно быть не длиннее, чем 20 символов.",
            maxLength(20),
          ),
          checkRegex: helpers.withMessage(
            "Имя пользователя может содержать только из латинские буквы, " +
              "цифры, а также следующие символы . @ + -",
            helpers.regex(/^[\w.@+-]+$/),
          ),
          $autoDirty: true,
        },
        email: {
          required: helpers.withMessage(
            "Введите адрес электронной почты.",
            required,
          ),
          email: helpers.withMessage(
            "Некорректный адрес электронной почты.",
            email,
          ),
          $autoDirty: true,
        },
        firstname: {
          required: helpers.withMessage("Введите своё имя.", required),
          $autoDirty: true,
        },
        lastname: {
          required: helpers.withMessage("Введите свою фамилию.", required),
          $autoDirty: true,
        },
        password: {
          required: helpers.withMessage("Введите пароль.", required),
          minLength: helpers.withMessage(
            "Пароль должен содержать от 8 символов.",
            minLength(8),
          ),
          checkRegex: helpers.withMessage(
            "Пароль должен состоять из латинских букв и содержать заглавную букву, цифру и спец. символ (@, $, !, %, *, ?, &).",
            helpers.regex(
              /^(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/,
            ),
          ),
          $autoDirty: true,
        },
        passwordConfirm: {
          required: helpers.withMessage("Повторите пароль.", required),
          sameAs: helpers.withMessage(
            "Пароли не совпадают.",
            sameAs(this.signUpData.password),
          ),
          $autoDirty: true,
        },
      },
    }
  },
}
</script>

<template>
  <div
    class="absolute top-0 -z-[101] h-full w-full animate-pulse bg-slate-950"></div>
  <img
    alt=""
    class="fixed top-0 -z-[100] h-full w-full select-none object-cover blur-[2px] brightness-[80%]"
    src="@/assets/images/background-1.png" />
  <div class="h-full min-h-[100vh] w-full pb-8 pt-2">
    <Container class="pt-[100px] sm:pt-[188px]">
      <div class="flex flex-col justify-center gap-8 md:flex-row">
        <div
          class="flex h-full w-full basis-3/6 animate-fade-up select-none flex-col gap-2.5 overflow-hidden rounded-xl bg-white px-4 pb-2 pt-2.5 text-center animate-delay-[300ms] animate-duration-[600ms] animate-once">
          <span class="text-[24px] font-bold">Регистрация</span>
          <form class="flex flex-col gap-2.5" method="post">
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]"
                >Уникальное имя пользователя</label
              >
              <input
                v-model="signUpData.username"
                :class="{
                  'border-red-600': v$.signUpData.username.$error,
                  'focus:border-red-600': v$.signUpData.username.$error,
                }"
                class="w-full rounded-[0.3rem] border-[1px] border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                placeholder="AceRevolutioner1991"
                type="text" />
              <div
                v-if="v$.signUpData.username.$error"
                class="flex w-full flex-col text-left text-[14px]">
                <span
                  v-for="error in v$.signUpData.username.$errors"
                  class="text-red-600">
                  {{ error.$message }}
                </span>
              </div>
            </div>
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]">Имя</label>
              <input
                v-model="signUpData.firstname"
                :class="{
                  'border-red-600': v$.signUpData.firstname.$error,
                  'focus:border-red-600': v$.signUpData.firstname.$error,
                }"
                class="w-full rounded-[0.3rem] border-[1px] border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                placeholder="Владимир"
                type="text" />
              <div
                v-if="v$.signUpData.firstname.$error"
                class="w-full text-left text-[14px]">
                <span
                  v-for="error in v$.signUpData.firstname.$errors"
                  class="text-[14px] text-red-600">
                  {{ error.$message }}
                </span>
              </div>
            </div>
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]">Фамилия</label>
              <input
                v-model="signUpData.lastname"
                :class="{
                  'border-red-600': v$.signUpData.lastname.$error,
                  'focus:border-red-600': v$.signUpData.lastname.$error,
                }"
                class="w-full rounded-[0.3rem] border-[1px] border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                placeholder="Ленин"
                type="text" />
              <div
                v-if="v$.signUpData.lastname.$error"
                class="w-full text-left text-[14px]">
                <span
                  v-for="error in v$.signUpData.lastname.$errors"
                  class="text-[14px] text-red-600">
                  {{ error.$message }}
                </span>
              </div>
            </div>
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]">Электронная почта</label>
              <input
                v-model="signUpData.email"
                :class="{
                  'border-red-600': v$.signUpData.email.$error,
                  'focus:border-red-600': v$.signUpData.email.$error,
                }"
                class="w-full rounded-[0.3rem] border-[1px] border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                placeholder="our.mail@party.comm"
                type="email" />
              <div
                v-if="v$.signUpData.email.$error"
                class="w-full text-left text-[14px]">
                <span
                  v-for="error in v$.signUpData.email.$errors"
                  class="text-[14px] text-red-600">
                  {{ error.$message }}
                </span>
              </div>
            </div>
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]"
                >Придумайте надежный пароль</label
              >
              <div class="flex flex-row">
                <input
                  v-if="password1Hidden"
                  v-model="signUpData.password"
                  :class="{
                    'border-red-600': v$.signUpData.password.$error,
                    'focus:border-red-600': v$.signUpData.password.$error,
                  }"
                  class="w-full rounded-l-[0.3rem] border-b border-l border-t border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                  placeholder="********"
                  type="password"
                  @focusin="password1Focused = !password1Focused"
                  @focusout="password1Focused = !password1Focused" />
                <input
                  v-else
                  v-model="signUpData.password"
                  :class="{
                    'border-red-600': v$.signUpData.password.$error,
                    'focus:border-red-600': v$.signUpData.password.$error,
                  }"
                  class="w-full rounded-l-[0.3rem] border-b border-l border-t border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                  placeholder="********"
                  type="text"
                  @focusin="password1Focused = !password1Focused"
                  @focusout="password1Focused = !password1Focused" />
                <div
                  :class="{
                    'border-[#4285F4]':
                      password1Focused && !v$.signUpData.password.$error,
                    'border-red-600': v$.signUpData.password.$error,
                  }"
                  class="flex aspect-square w-7 cursor-pointer items-center justify-center rounded-r-[0.3rem] border-b border-r border-t border-[#ADADAD] pr-1">
                  <i
                    :class="password1Hidden ? 'bi-eye' : 'bi-eye-slash'"
                    class="bi block text-black"
                    @click.prevent="password1Hidden = !password1Hidden"></i>
                </div>
              </div>
              <div
                v-if="v$.signUpData.password.$error"
                class="flex w-full flex-col text-left text-[14px]">
                <span
                  v-for="error in v$.signUpData.password.$errors"
                  class="text-red-600">
                  - {{ error.$message }}
                </span>
              </div>
            </div>
            <div class="flex flex-col gap-0.5">
              <label class="text-start text-[14px]">Повторите пароль</label>
              <div class="flex flex-row">
                <input
                  v-if="password2Hidden"
                  v-model="signUpData.passwordConfirm"
                  :class="{
                    'border-red-600': v$.signUpData.passwordConfirm.$error,
                    'focus:border-red-600':
                      v$.signUpData.passwordConfirm.$error,
                  }"
                  class="w-full rounded-l-[0.3rem] border-b border-l border-t border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                  placeholder="********"
                  type="password"
                  @focusin="password2Focused = !password2Focused"
                  @focusout="password2Focused = !password2Focused" />
                <input
                  v-else
                  v-model="signUpData.passwordConfirm"
                  :class="{
                    'border-red-600': v$.signUpData.passwordConfirm.$error,
                    'focus:border-red-600':
                      v$.signUpData.passwordConfirm.$error,
                  }"
                  class="w-full rounded-l-[0.3rem] border-b border-l border-t border-[#ADADAD] px-2 py-1.5 text-[14px] focus:border-[#4285F4]"
                  placeholder="********"
                  type="text"
                  @focusin="password2Focused = !password2Focused"
                  @focusout="password2Focused = !password2Focused" />
                <div
                  :class="{
                    'border-[#4285F4]':
                      password2Focused && !v$.signUpData.passwordConfirm.$error,
                    'border-red-600': v$.signUpData.passwordConfirm.$error,
                  }"
                  class="flex aspect-square w-7 cursor-pointer items-center justify-center rounded-r-[0.3rem] border-b border-r border-t border-[#ADADAD] pr-1">
                  <i
                    :class="password2Hidden ? 'bi-eye' : 'bi-eye-slash'"
                    class="bi block text-black"
                    @click.prevent="password2Hidden = !password2Hidden"></i>
                </div>
              </div>
              <div
                v-if="v$.signUpData.passwordConfirm.$error"
                class="flex w-full flex-col text-left text-[14px]">
                <span
                  v-for="error in v$.signUpData.passwordConfirm.$errors"
                  class="text-red-600">
                  - {{ error.$message }}
                </span>
              </div>
            </div>
            <button
              class="w-full rounded-[0.3rem] bg-[#4B7DDD] py-1.5 text-[14px] font-medium text-white transition-all duration-150 ease-in-out hover:drop-shadow-md active:bg-[#21B3E2] active:drop-shadow-none"
              type="submit"
              @click.prevent="signUp">
              Создать аккаунт
            </button>
            <span class="text-[14px]"
              >У вас уже есть аккаунт?&nbsp;
              <span
                class="cursor-pointer text-[#E9583B] hover:underline"
                @click="toSignInPage()"
                >Войти</span
              >
            </span>
          </form>
        </div>
        <div class="flex basis-3/6 select-none flex-col gap-3">
          <span class="text-[24px] font-medium text-white 2xl:text-[26px]"
            >Добро пожаловать!</span
          >
          <p
            class="select-none text-justify text-[16px] font-normal text-white 2xl:text-[18px]">
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

<style scoped></style>
