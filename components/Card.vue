<template>
    <div class="greeting-animation">
        <div v-for="(greeting, index) in visibleGreetings" :key="index" :style="getRandomPosition()"
            class="greeting-message">
            {{ greeting }}
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            greetings: [
                "Chúc mừng năm mới!",
                "Chúc bạn một năm mới tràn đầy niềm vui!",
                "Hy vọng bạn có một năm mới tuyệt vời!",
                // Thêm các lời chúc khác vào đây
            ],
            visibleGreetings: [],
        };
    },
    mounted() {
        this.showGreetingsSequentially(0);
    },
    methods: {
        showGreetingsSequentially(index) {
            if (index < this.greetings.length) {
                this.visibleGreetings.push(this.greetings[index]);

                // Hiển thị lời chúc tiếp theo sau 1 giây
                setTimeout(() => {
                    this.showGreetingsSequentially(index + 1);
                }, 1000);
            }
        },
        getRandomPosition() {
            const top = Math.random() * (window.innerHeight - 50); // 50 là chiều cao của lời chúc
            const left = Math.random() * (window.innerWidth - 200); // 200 là chiều rộng của lời chúc
            return {
                top: `${top}px`,
                left: `${left}px`,
            };
        },
    },
};
</script>
  
<style scoped>
.greeting-animation {
    position: relative;
    height: 100vh;
    /* Chiều cao bằng chiều cao của màn hình */
    overflow: hidden;
    /* Ẩn phần nội dung vượt quá chiều cao */
}

.greeting-message {
    position: absolute;
    background: rgba(255, 255, 255, 0.8);
    padding: 10px;
    box-sizing: border-box;
    opacity: 0;
    /* Bắt đầu ẩn */
    margin-bottom: 20px;
    /* Khoảng cách giữa các lời chúc */
    animation: move-up 5s linear;
    /* 5 giây cho mỗi lời chúc */
}

@keyframes move-up {

    0%,
    100% {
        top: 100%;
        opacity: 0;
    }

    10%,
    90% {
        top: 0;
        opacity: 1;
    }
}</style>
  