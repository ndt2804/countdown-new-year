<!-- <template>
    <div class="flex items-center justify-center ">
        <div class="block m-2">
            <p class="digit text-teal-500 text-6xl font-thin">{{ days | twoDigits }}</p>
            <p class="text-center text-teal-500 text-2xl font-thin">Days</p>
        </div>
        <span class="text-center text-teal-500 text-6xl font-thin">:</span>
        <div class="block m-2">
            <p class="digit text-teal-500 text-6xl font-thin">{{ hours | twoDigits }}</p>
            <p class="text-center text-teal-500 text-2xl font-thin">Hours</p>
        </div>
        <span class="text-center text-teal-500 text-6xl font-thin">:</span>
        <div class="block m-2">
            <p class="digit text-teal-500 text-6xl font-thin">{{ minutes | twoDigits }}</p>
            <p class="text-center text-teal-500 text-2xl font-thin">Minutes</p>
        </div>
        <span class="text-center text-teal-500 text-6xl font-thin">:</span>
        <div class="block m-2">
            <p class="digit text-teal-500 text-6xl font-thin">{{ seconds | twoDigits }}</p>
            <p class="text-center text-teal-500 text-2xl font-thin">Seconds</p>
        </div>
    </div>
</template> -->
<template>
    <div>
        <!-- <seciton class="text-3xl flex justify-center content-center flex-col mx-auto text-center">
            Happy New Years
        </seciton> -->
        <seciton class="flex text-6xl justify-center content-center">
            <div class="days mr-2 relative">
                {{ days | twoDigits }}
                <div class="label text-sm absolute mt-2">days</div>
            </div>
            <span class="mb-2">:</span>
            <div class="hours mx-2 relative">
                {{ hours | twoDigits }}
                <div class="label text-sm absolute mt-2">hours</div>
            </div>
            <span class="mb-2">:</span>
            <div class="minutes mx-2 relative">
                {{ minutes | twoDigits }}
                <div class="label text-sm absolute mt-2">minutes</div>
            </div>
            <span class="mb-2">:</span>
            <div class="seconds ml-2 relative">
                <div> {{ seconds | twoDigits }}
                </div>
                <div class="label text-sm absolute mt-2">seconds</div>
            </div>
        </seciton>
    </div>
</template>
  
  
  
  
  
  

  
  
<script>
export default {
    props: {
        targetDate: {
            type: String,
            required: true,
        },
    },

    data() {
        return {
            now: Math.trunc(new Date().getTime() / 1000),
        };
    },

    created() {
        setInterval(() => {
            this.now = Math.trunc(new Date().getTime() / 1000);
        }, 1000);
    },

    computed: {
        seconds() {
            return (this.targetTimestamp - this.now) % 60;
        },

        minutes() {
            return Math.trunc((this.targetTimestamp - this.now) / 60) % 60;
        },

        hours() {
            return Math.trunc((this.targetTimestamp - this.now) / 60 / 60) % 24;
        },

        days() {
            return Math.trunc((this.targetTimestamp - this.now) / 60 / 60 / 24);
        },

        targetTimestamp() {
            return Math.trunc(Date.parse(this.targetDate) / 1000);
        },
    },

    filters: {
        twoDigits(value) {
            return value < 10 ? `0${value}` : value;
        },
    },
};
</script>