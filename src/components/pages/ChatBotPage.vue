<script>
export default {
    name: "ChatBotPage",
    data () {
        return {
            variants: ['1 вариант', '2 вариант', '3 вариант', '4 вариант', '5 вариант'],
            selectVariant: null,
            showSelected: true,
            typing: true,
        }
    },
    methods: {
        submit () {
            const el = this.$refs.chatbox
            this.typing = false;
            this.showSelected = false;
            setTimeout(() => {
                el.scrollTo(0, el.scrollHeight);
            }, 100);
        }
    },
    created () {
        setTimeout(() => {
            const el = this.$refs.chatbox
            el.scrollTo(0, el.scrollHeight);
        }, 500);
    }
}
</script>
<template>
    <Container class="pt-[120px] sm:pt-[168px] pb-[20px] sm:pb-[50px] font-roboto">
        <div class="relative max-w-[1096px] mx-auto">
            <div
                ref="chatbox"
                class="max-h-[590px] overflow-y-scroll scrolbar-hide scroll-smooth bg-[#E4ECF4] px-[23px] pt-[49px] rounded-[20px]"
                :class="!showSelected ? 'pb-[100px] sm:pb-[105px] lg:pb-[110px]' : 'pb-[170px] sm:pb-[275px] lg:pb-[153px]'"
            >
                <div class=" flex flex-col gap-[28px]">
                    <!-- Bot -->
                    <div class="flex items-start gap-[20px]">
                        <div class="w-[57px] h-[57px] shrink-0">
                            <img src="@/assets/images/bot-logo.svg" class="w-full h-full object-cover" alt="">
                        </div>
                        <div class="flex flex-col items-start gap-[15px] text-[16px] sm:text-[20px] font-[500]">
                            <div class="bg-white rounded-[10px_30px_30px_30px] pt-[23px] pb-[24px] ps-[25px] pe-[42px]">
                                Добро пожаловать! Давайте найдем вам идеальный тур.
                            </div>
                            <div class="bg-white rounded-[10px_30px_30px_30px] pt-[23px] pb-[24px] ps-[25px] pe-[42px]">
                                Как вы хотите провести своё путешествие?
                            </div>
                        </div>
                    </div>
                    <!-- Bot end -->

                    <!-- User -->
                    <div v-if="!typing" class="flex items-start gap-[20px]">
                        <div class="w-[57px] h-[57px] shrink-0">
                            <img src="@/assets/images/user-logo.svg" class="w-full h-full object-cover" alt="">
                        </div>
                        <div class="flex flex-col items-start gap-[15px]">
                            <div class="text-[20px] font-[500] bg-white rounded-[10px_30px_30px_30px] py-[19px] ps-[25px] pe-[40px]">
                                <ul class="flex flex-col gap-[12px] sm:gap-[17px]">
                                    <li
                                        v-for="i in variants"
                                        :key="i"
                                        class="flex items-center gap-[22px]"
                                    >
                                        <span
                                            class="flex items-center justify-center rounded-full border-[2px] border-solid border-[#027AD0] w-[30px] h-[30px] shrink-0"
                                            :class="i == selectVariant ? 'bg-[#027AD0]' : ''"
                                        >
                                            <img v-if="i == selectVariant" src="@/assets/images/white-check.svg" alt="">
                                        </span>
                                        <span class="text-[16px] sm:text-[20px] font-[500]">
                                            {{ i }}
                                        </span>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                    <!-- User end -->

                    <!-- User typing -->
                    <div v-else class="flex flex-row-reverse items-start gap-[20px]">
                        <div class="w-[57px] h-[57px] shrink-0">
                            <img src="@/assets/images/user-logo.svg" class="w-full h-full object-cover" alt="">
                        </div>
                        <div class="flex flex-col items-start gap-[15px]">
                            <div class="text-[30px] sm:text-[40px] font-[700] bg-white rounded-[30px_10px_30px_30px] pt-[11px] pb-[12px] ps-[69px] pe-[76px]">
                                ...
                            </div>
                        </div>
                    </div>
                    <!-- User typing end -->
                </div>
            </div>

            <div
                class="absolute flex items-end sm:items-center gap-[18px] justify-between bg-white w-[calc(100%_-_46px)] rounded-[10px] pt-[18px] pe-[10px] pb-[16px] ps-[20px] bottom-[23px] left-[23px]"
                :class="!showSelected ? 'pt-[7px] pb-[6px] bottom-[15px]' : ''"
            >
                <!-- Write sms -->
                <div 
                    v-if="showSelected"
                    class="flex w-full h-[100px] sm:h-auto overflow-y-scroll sm:overflow-y-visible scrolbar-hide flex-wrap lg:flex-nowrap gap-[9px]"
                >
                    <button
                        v-for="i in variants"
                        :key="i"
                        @click="selectVariant = i"
                        class="bg-[#EEEEEE] w-full sm:w-[calc(50%_-_4.5px)] lg:w-full h-[30px] sm:h-[59px] rounded-[20px] text-[16px] sm:text-[20px] font-[700]"
                        :class="selectVariant == i ? 'border border-solid border-[#4285F4]' : ''"
                    >
                        {{i}}
                    </button>
                </div>
                <div v-else class="w-full">
                    <input type="text" :placeholder="selectVariant" class="w-full text-[14px] sm:text-[18px] h-[45px] sm:h-auto">
                </div>
                <!-- Write sms end -->

                <button
                    @click="submit()"
                    class="bg-[#EF533F] w-[100px] sm:w-[172px] shrink-0 py-[12px] sm:py-[17px] rounded-[5px] font-[700] text-[14px] sm:text-[18px] text-white"
                    :class="!showSelected ? 'py-[10px] sm:pt-[13px] sm:pb-[14px]' : ''"
                    :disabled="!selectVariant"
                >
                    Отправить
                </button>
            </div>
        </div>

    </Container>
</template>