<template>
    <div>
        <section class="text-3xl flex justify-center items-center flex-col mx-auto text-center">
            Happy New Years
        </section>

        <section class="flex text-6xl justify-center items-center">
            <div class="relative flex items-center">
                <div v-if="isNewMinute" class="animated-number mr-2 relative" :class="{ 'animated': showAnimation }"
                    ref="animatedNumber">
                    {{ animatedDigit }}
                    <div class="label text-sm absolute bottom-0">minutes</div>
                </div>
                <span v-else class="leading-snug">:</span>
                <div class="hours mx-2 relative">
                    {{ hours | twoDigits }}
                    <div class="label text-sm absolute bottom-0">hours</div>
                </div>
                <span class="leading-snug">:</span>
                <div class="minutes mx-2 relative">
                    {{ minutes | twoDigits }}
                    <div class="label text-sm absolute bottom-0">minutes</div>
                </div>
                <span class="leading-snug">:</span>
                <div class="seconds ml-2 relative">
                    {{ seconds | twoDigits }}
                    <div class="label text-sm absolute bottom-0">seconds</div>
                </div>
            </div>
        </section>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            isNewMinute: false,
            showAnimation: false,
            animatedDigit: 5, // Starting digit before animation
        };
    },
    computed: {
        animatedNumber() {
            return this.showAnimation ? this.animatedDigit : this.animatedDigit - 1;
        },
    },
    methods: {
        startNewMinuteAnimation() {
            // Trigger animation when it's time for a new minute
            this.isNewMinute = true;

            // Simulate countdown
            const countdownInterval = setInterval(() => {
                this.showAnimation = !this.showAnimation;
                if (this.showAnimation) {
                    this.animatedDigit++;
                    if (this.animatedDigit > 9) {
                        // Reset digit after reaching 9
                        this.animatedDigit = 0;
                    }
                }
            }, 1000);

            // Stop animation after a certain duration (e.g., 1 minute)
            setTimeout(() => {
                clearInterval(countdownInterval);
                this.isNewMinute = false;
                this.showAnimation = false;
            }, 60000); // 1 minute
        },
    },
    watch: {
        // Watch the 'isNewMinute' flag and start the animation when it becomes true
        isNewMinute(newValue) {
            if (newValue) {
                this.startNewMinuteAnimation();
            }
        },
    },
    created() {
        // Update 'isNewMinute' flag every minute
        setInterval(() => {
            const now = new Date();
            if (now.getSeconds() === 0) {
                this.isNewMinute = true;
            }
        }, 1000);
    },
};
</script>
  
<style>
.animated {
    animation: slideUp 1s ease-in-out infinite alternate;
}

@keyframes slideUp {
    from {
        transform: translateY(0);
    }

    to {
        transform: translateY(-1em);
    }
}
</style>
  