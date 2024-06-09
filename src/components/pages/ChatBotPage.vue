<script>
export default {
    name: "ChatBotPage"
}
</script>
<template>
    <Container class="pt-[168px] pb-[50px] font-roboto">
        <div class="relative">
            <div class="max-h-[590px] overflow-y-scroll scrolbar-hide bg-[#E4ECF4] px-[23px] pt-[49px] pb-[153px] rounded-[20px]">
                <div class=" flex flex-col gap-[28px]">
                    <!-- Bot -->
                    <div class="flex items-start gap-[20px]">
                        <div class="w-[57px] h-[57px] shrink-0">
                            <img src="@/assets/images/bot-logo.svg" class="w-full h-full object-cover" alt="">
                        </div>
                        <div class="flex flex-col items-start gap-[15px]">
                            <div class="text-[20px] font-[500] bg-white rounded-[10px_30px_30px_30px] pt-[23px] pb-[24px] ps-[25px] pe-[42px]">
                                Добро пожаловать! Давайте найдем вам идеальный тур.
                            </div>
                            <div class="text-[20px] font-[500] bg-white rounded-[10px_30px_30px_30px] pt-[23px] pb-[24px] ps-[25px] pe-[42px]">
                                Как вы хотите провести своё путешествие?
                            </div>
                        </div>
                    </div>
                    <!-- Bot end -->

                    <!-- User -->
                    <div class="flex items-start gap-[20px]">
                        <div class="w-[57px] h-[57px] shrink-0">
                            <img src="@/assets/images/user-logo.svg" class="w-full h-full object-cover" alt="">
                        </div>
                        <div class="flex flex-col items-start gap-[15px]">
                            <div class="text-[20px] font-[500] bg-white rounded-[10px_30px_30px_30px] pt-[23px] pb-[24px] ps-[25px] pe-[42px]">
                                Добро пожаловать! Давайте найдем вам идеальный тур.
                            </div>
                            <div class="text-[20px] font-[500] bg-white rounded-[10px_30px_30px_30px] pt-[23px] pb-[24px] ps-[25px] pe-[42px]">
                                Как вы хотите провести своё путешествие?
                            </div>
                        </div>
                    </div>
                    <!-- User end -->

                    <!-- User typing -->
                    <div class="flex flex-row-reverse items-start gap-[20px]">
                        <div class="w-[57px] h-[57px] shrink-0">
                            <img src="@/assets/images/user-logo.svg" class="w-full h-full object-cover" alt="">
                        </div>
                        <div class="flex flex-col items-start gap-[15px]">
                            <div class="text-[40px] font-[700] bg-white rounded-[30px_10px_30px_30px] pt-[11px] pb-[12px] ps-[69px] pe-[76px]">
                                ...
                            </div>
                        </div>
                    </div>
                    <!-- User typing end -->
                </div>
            </div>

            <div class="absolute flex items-center justify-between bg-white w-[calc(100%_-_46px)] rounded-[10px] pt-[18px] pe-[10px] pb-[16px] ps-[20px] bottom-[23px] left-[23px]">
                <!-- Write sms -->
                
                <!-- Write sms end -->
                <button
                    class="bg-[#EF533F] w-[172px] py-[17px] rounded-[5px] font-[700] text-[18px] text-white"
                >
                    Отправить
                </button>
            </div>
        </div>

    </Container>
</template>