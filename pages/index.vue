<template>
    <!-- <div class="container h-screen flex items-center justify-center mx-auto ">
        <div>
            <img alt="hero image" src="~/assets/new-year.png" width="300" height="300" />
            <Countdown targetDate="February 10, 2024"></Countdown>
            
        </div>
    </div> -->
    <div>
        <div class="min-h-screen flex items-center justify-center bg-black text-white font-work-sans font-extrabold">
            <div>

                <p class="text-8xl uppercase text-center leading-none">Happy New Year <span class="fancy block">2024</span>

                </p>
                <div class="pt-10">
                    <Count :year="2024" :month="1" :date="9" :hour="23" :minute="59" :second="59" :millisecond="59" />

                </div>

            </div>


        </div>

    </div>
</template>
<style>
.fancy {
    @supports (background-clip: text) or (-webkit-background-clip: text) {
        background-image:
            url("data:image/svg+xml,%3Csvg width='2250' height='900' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cg%3E%3Cpath fill='%2300A080' d='M0 0h2255v899H0z'/%3E%3Ccircle cx='366' cy='207' r='366' fill='%2300FDCF'/%3E%3Ccircle cx='1777.5' cy='318.5' r='477.5' fill='%2300FDCF'/%3E%3Ccircle cx='1215' cy='737' r='366' fill='%23008060'/%3E%3C/g%3E%3C/svg%3E%0A");
        background-size: 110% auto;
        background-position: center;
        color: transparent;
        -webkit-background-clip: text;
        background-clip: text;
    }
}
</style>

