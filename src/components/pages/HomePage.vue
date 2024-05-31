<script>
    // Import Swiper Vue.js components
    import { Swiper, SwiperSlide } from 'swiper/vue';

    // Import Swiper styles
    import 'swiper/css';

export default {
    name: "HomePage",
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        return {};
    },
    data () {
        return {
            tours: [
                {
                    discount: '-51%',
                    date: '28.05.2024',
                    to: 'Горящие туры в Турцию из',
                    from: 'Алматы',
                    oldPrice: '1 439 097〒',
                    price: '953 284〒',
                    img: 1,
                },
                {
                    discount: '-47%',
                    date: '28.05.2024',
                    to: 'Горящие туры на',
                    from: 'Мальдивы из Алматы',
                    oldPrice: '1 140 134〒',
                    price: '778 150〒',
                    img: 2,
                },
                {
                    discount: '-14%',
                    date: '14.08.2024',
                    to: 'Горящие туры в Турцию из',
                    from: 'Астаны',
                    oldPrice: '991 958〒',
                    price: '867 479〒',
                    img: 3,
                },
                {
                    discount: '-24%',
                    date: '24.05.2024',
                    to: 'Горящие туры в Египет из',
                    from: 'Алматы',
                    oldPrice: '906 504〒',
                    price: '730 541〒',
                    img: 4,
                },
                {
                    discount: '-7%',
                    date: '25.05.2024',
                    to: 'Горящие туры в Тайланд',
                    from: 'из Астаны',
                    oldPrice: '1 734 064〒',
                    price: '1 617 969〒',
                    img: 5,
                },
                {
                    discount: '-6%',
                    date: '25.05.2024',
                    to: 'Горящие туры во Вьетнам',
                    from: 'из Алматы',
                    oldPrice: '996 486〒',
                    price: '939 546〒',
                    img: 6,
                },
                {
                    discount: '-6%',
                    date: '25.05.2024',
                    to: 'Горящие туры в Турцию из',
                    from: 'Алматы',
                    oldPrice: '1 439 097〒',
                    price: '953 284〒',
                    img: 7,
                },
            ],
            lowest: [
                {
                    country: 'Абхазия',
                    from: 'из Москвы',
                    date: '29 Мая',
                    time: '7 ночей',
                    price: '10 942',
                    img: 1
                },
                {
                    country: 'Россия',
                    from: 'из Москвы',
                    date: '29 Мая',
                    time: '6 ночей',
                    price: '11 035',
                    img: 2
                },
                {
                    country: 'Красная Поляна',
                    from: 'Россия из Москвы',
                    date: '29 Мая',
                    time: '6 ночей',
                    price: '13 316',
                    img: 3
                },
                {
                    country: 'Турция',
                    from: 'из Москвы',
                    date: '24 Мая',
                    time: '7 ночей',
                    price: '23 248',
                    img: 4
                },
                {
                    country: 'Катар',
                    from: 'из Москвы',
                    date: '31 Мая',
                    time: '7 ночей',
                    price: '25 841',
                    img: 5
                },
                {
                    country: 'Мармарис',
                    from: 'Турция из Москвы',
                    date: '24 Мая',
                    time: '6 ночей',
                    price: '28 567',
                    img: 6
                },
                {
                    country: 'ОАЭ',
                    from: 'из Москвы',
                    date: '27 Мая',
                    time: '6 ночей',
                    price: '29 379',
                    img: 7
                },
                {
                    country: 'Шарджа',
                    from: 'ОАЭ из Москвы',
                    date: '23 Мая',
                    time: '6 ночей',
                    price: '29 705',
                    img: 8
                },
                {
                    country: 'Бахрейн',
                    from: 'из Москвы',
                    date: '31 Мая',
                    time: '7 ночей',
                    price: '36 131',
                    img: 9
                },
                {
                    country: 'Египет',
                    from: 'из Москвы',
                    date: '24 Мая',
                    time: '6 ночей',
                    price: '37 732',
                    img: 10
                },
                {
                    country: 'Хургада',
                    from: 'Египет из Москвы',
                    date: '27 Мая',
                    time: '6 ночей',
                    price: '42 877',
                    img: 11
                },
                {
                    country: 'Армения',
                    from: 'из Москвы',
                    date: '29 Мая',
                    time: '6 ночей',
                    price: '44 372',
                    img: 12
                },
            ],
            dateValue: '',
            hotel: 1
        }
    }
}
</script>

<template>
    <div class="w-full overflow-hidden">
        <!-- Home -->
        <section class="relative z-[1] mb-[50px] lg:mb-[67px]">
            <img src="@/assets/images/home-background.png" class="absolute z-[-1] top-0 left-0 w-full h-full object-cover object-[center_top]" alt="">
            <div class="max-w-[calc(100%_-_40px)] lg:max-w-[calc(100%_-_100px)] xl:max-w-[1124px] pt-[100px] md:pt-[150px] lg:pt-[200px] xl:pt-[238px] pb-[80px] md:pb-[100px] lg:pb-[120px] xl:pb-[152px] mx-auto">
                <h1 class="font-roboto text-white text-[42px] md:text-[72px] xl:text-[96px] font-bold mb-[30px]">Откройте Мир с <br> STUAIR</h1>
                <div class="relative pt-[20px] lg:pt-[57px] px-[20px] lg:px-[44px] pb-[60px] lg:pb-[93px] bg-blue rounded-[20px]">
                    <div class="relative">
                        <input
                            type="text"
                            placeholder="Поиск туров и курортов"
                            class="bg-white w-full h-[50px] lg:h-[71px] ps-[20px] ps-[42px] pe-[50px] lg:pe-[94px] rounded-[10px] font-roboto text-[14px] lg:text-[18px]"
                        >
                        <orange-button class="absolute flex items-center justify-center right-[6px] lg:right-[12px] top-[6px] lg:top-[11px] max-w-[38px] lg:w-[172px] h-[38px] lg:h-[48px] p-0 px-0">
                            <span class="hidden lg:block">Поиск</span>
                            <img class="lg:hidden shrink-0 min-w-[16px]" src="@/assets/images/search.svg" alt="">
                        </orange-button>
                    </div>
                </div>
            </div>
        </section>
        <!-- Home end -->

        <!-- Tours -->
        <section id="tours" class="pb-[50px] lg:pb-[78px]">
            <div class="mb-[30px] lg:mb-[43px] max-w-[calc(100%_-_40px)] lg:max-w-[calc(100%_-_100px)] xl:max-w-[1160px] mx-auto">
                <h2 class="font-roboto text-[36px] font-[500] text-[#282828] leading-[62.4px]">Горящие туры</h2>
            </div>
            <div class="max-w-[calc(100%_-_40px)] lg:max-w-[calc(100%_-_100px)] 2xl:max-w-[1590px] mx-auto relative">
                <swiper
                    :slidesPerView="1"
                    :spaceBetween="10"
                    :loop="true"
                    :initialSlide="1"
                    :breakpoints="{
                        '700': {
                            slidesPerView: 2
                        },
                        '1040': {
                            slidesPerView: 3,
                        },
                        '1355': {
                            slidesPerView: 4
                        },
                        '1550': {
                            slidesPerView: 5
                        },

                    }"
                    class="mySwiper"
                    style="overflow: visible !important;"
                >
                    <swiper-slide v-for="(tour, idx) in tours" :key="idx">
                        <div class="relative border-2 border-solid border-[#F3F3F3] rounded-[12px] overflow-hidden font-source-sans-pro">
                            <div class="absolute top-0 left-[25px] z-[1]">
                                <img src="@/assets/images/discount-icon.svg" alt="">
                                <span class="absolute left-[5.16px] top-[9.75px] text-[13px] text-white">{{ tour.discount }}</span>
                            </div>
                            <img :src="`src/assets/images/tour_card_${tour.img}.png`" class="h-[200px] w-full object-cover" alt="">
                            <div class="p-[16px]">
                                <div class="flex items-center gap-[10px] mb-[10.5px]">
                                    <img src="@/assets/images/fly.svg" alt="">
                                    <div class="text-[14px] text-light-blue">Вылет из Алматы - <span class="text-orange">{{ tour.date }}</span></div>
                                </div>
                                <div class="min-h-[94px] mb-[8px] text-[23px] font-[400]">
                                    <div class="">{{ tour.to }}</div>
                                    <div>{{ tour.from }}</div>
                                </div>
                                <div class="flex justify-between items-end">
                                    <div class="flex flex-col text-[#282828] text-[18px] font-[400]">
                                        <span class="mb-[1px] text-[#6F7893] text-[14px] line-through">{{ tour.oldPrice }}</span>
                                        {{ tour.price }}
                                    </div>
                                    <orange-button>Забронировать</orange-button>
                                </div>
                            </div>
                        </div>
                    </swiper-slide>
                </swiper>
            </div>
        </section>
        <!-- Tours end -->

        <!-- Lowest prices -->
        <section id="country">
            <div class="max-w-[calc(100%_-_40px)] xl:max-w-[1160px] mx-auto">
                <h2 class="text-[#2B3F5A] font-roboto text-[36px] font-[500] leading-[34px] mb-[19px]">Самые низкие цены</h2>

                <div class="bg-[#F4F7FB] p-[10px] rounded-[15px] mb-[20px] font-montserrat flex flex-wrap xl:flex-nowrap items-center gap-[10px]">
                    <select class="w-full sm:w-[calc(50%_-_5px)] md:w-[calc(100%_/_3_-_20px_/_3)] xl:w-full bg-light border border-gray-300 text-[#5C6672] text-[13px] rounded-[3px] block w-full px-[10px] py-[9px]">
                        <option hidden>Город вылета</option>
                        <option>Canada</option>
                        <option>France</option>
                        <option>Germany</option>
                    </select>
                    <select class="w-full sm:w-[calc(50%_-_5px)] md:w-[calc(100%_/_3_-_20px_/_3)] xl:w-full bg-light border border-gray-300 text-[#5C6672] text-[13px] rounded-[3px] block w-full px-[10px] py-[9px]">
                        <option hidden>Страна</option>
                        <option>Canada</option>
                        <option>France</option>
                        <option>Germany</option>
                    </select>
                    <div class="w-full sm:w-[calc(50%_-_5px)] md:w-[calc(100%_/_3_-_20px_/_3)] xl:w-full">
                        <vue-tailwind-datepicker
                            v-model="dateValue"
                            placeholder="Даты вылета"
                            as-single
                            inputClasses="text-[13px] h-[38px] px-[10px] border border-gray-300 text-[#5C6672] placeholder-[#5C6672] rounded-[3px]"
                        />
                    </div>
                    <div class="flex items-center justify-between w-full sm:w-[calc(50%_-_5px)] md:w-[calc(100%_/_3_-_20px_/_3)] xl:w-full bg-white border border-gray-300 text-[#5C6672] text-[13px] rounded-[3px] block w-full px-[10px] py-[9px]">
                        <span class="leading-[18px]">Отель</span>
                        <div class="flex items-center gap-[2px]">
                            <button @click="hotel = 1">
                                <img src="@/assets/images/star.svg" alt="" :class="`${hotel < 1 ? 'opacity-0' : ''}`">
                            </button>
                            <img src="@/assets/images/line.svg" alt="">
                            <button @click="hotel = 2">
                                <img src="@/assets/images/star.svg" alt="" :class="`${hotel < 2 ? 'opacity-0' : ''}`">
                            </button>
                            <img src="@/assets/images/line.svg" alt="">
                            <button @click="hotel = 3">
                                <img src="@/assets/images/star.svg" alt="" :class="`${hotel < 3 ? 'opacity-0' : ''}`">
                            </button>
                            <img src="@/assets/images/line.svg" alt="">
                            <button @click="hotel = 4">
                                <img src="@/assets/images/star.svg" alt="" :class="`${hotel < 4 ? 'opacity-0' : ''}`">
                            </button>
                            <img src="@/assets/images/line.svg" alt="">
                            <button @click="hotel = 5">
                                <img src="@/assets/images/star.svg" alt="" :class="`${hotel < 5 ? 'opacity-0' : ''}`">
                            </button>
                        </div>
                    </div>
                    <select class="w-full sm:w-[calc(50%_-_5px)] md:w-[calc(100%_/_3_-_20px_/_3)] xl:w-full bg-light border border-gray-300 text-[#5C6672] text-[13px] rounded-[3px] block w-full px-[10px] py-[9px]">
                        <option hidden>Бюджет (РУБ)</option>
                        <option>1 000 РУБ</option>
                        <option>10 000 РУБ</option>
                        <option>100 000 РУБ</option>
                    </select>
                    <button class="w-full sm:w-[calc(50%_-_5px)] md:w-[calc(100%_/_3_-_20px_/_3)] xl:w-full flex items-center justify-between h-[38px] bg-[#fff] border border-gray-300 text-[#5C6672] text-[13px] rounded-[3px] block w-full px-[10px] py-[9px]">
                        <span >Показать фильтры</span>
                        <img src="@/assets/images/filter-icon.svg" alt="">
                    </button>
                </div>

                <div class="flex flex-wrap gap-[20px] pb-[20px]">
                    <div
                        v-for="(item, idx) in lowest"
                        :key="idx"
                        class="relative overflow-hidden w-full sm:w-[calc(50%_-_10px)] md:w-[calc(100%_/_3_-_40px_/_3)] lg:w-[calc(25%_-_15px)] shadow-[0px_10px_25px_rgba(43,63,90,0.07)] p-[14px] rounded-[15px] font-montserrat"
                    >
                        <img :src="`src/assets/images/lowest_card_${item.img}.png`" alt="" class="w-full h-[154px] object-cover rounded-[10px] mb-[17px]">
                        <h3 class="text-[15px] font-[700] mb-[7px]">{{ item.country }}</h3>
                        <p class="text-[#808C9C] text-[14px] font-[500] mb-[7px]">{{ item.from }}</p>
                        <p class="bg-[#EEF2F8] inline-flex px-[10px] py-[7px] rounded-full text-[#333333] text-[13px] font-[400] gap-[7px] mb-[5px]">
                            <img src="@/assets/images/date-icon.svg" alt="">
                            {{ item.date }}
                        </p>
                        <br>
                        <p class="bg-[#EEF2F8] inline-flex px-[10px] py-[7px] rounded-full text-[#333333] text-[13px] font-[400] gap-[7px]">
                            <img src="@/assets/images/time-icon.svg" alt="">
                            {{ item.time }}
                        </p>
                        <div class="absolute bottom-0 right-0 bg-orange text-white rounded-[15px_0_0_0] flex items-center gap-[4px] font-[600] px-[15px]">
                            <span class="text-[16px] leading-[30px]">{{ item.price }}</span>
                            <span class="text-[9px]">руб</span>
                        </div>
                    </div>
                </div>

                <!-- Show more -->
                <div class="flex items-center gap-[14px] pb-[20px]">
                    <div class="w-full h-[1px] bg-[#DDDDDD]"></div>
                    <button class="shrink-0 border border-solid border-[#DDDDDD] h-[30px] rounded-full font-montserrat text-[10px] font-[400] px-[31px] uppercase bg-[#EFEFEF]">Показать все</button>
                    <div class="w-full h-[1px] bg-[#DDDDDD]"></div>
                </div>
                <!-- Show more end -->
            </div>
        </section>
        <!-- Lowest prices end -->

    </div>
</template>