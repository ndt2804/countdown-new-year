<template>
    <div class="container h-screen flex items-center justify-center mx-auto">
        <div class="mx-auto">
            <img alt="hero image" src="~/assets/new-year.png" width="600" height="600" />

        </div>


    </div>
</template>
<style scoped>
.card {
    position: relative;
    width: 300px;
    height: 200px;
    overflow: hidden;
}

.message {
    position: absolute;
    bottom: 0;
    width: 100%;
    background: rgba(255, 255, 255, 0.8);
    padding: 10px;
    box-sizing: border-box;
}

.slide-up-enter-active,
.slide-up-leave-active {
    transition: transform 1s ease-in-out;
}

.slide-up-enter,
.slide-up-leave-to {
    transform: translateY(100%);
}
</style>

<script>
// import { tsParticles } from "https://cdn.jsdelivr.net/npm/@tsparticles/engine@3.0.0/+esm";
// import { loadAll } from "https://cdn.jsdelivr.net/npm/@tsparticles/all@3.0.0/+esm";
import { tsParticles } from "@tsparticles/engine";
import { loadAll } from "@tsparticles/all";
async function loadParticles(options) {
    await loadAll(tsParticles);

    await tsParticles.load({ id: "tsparticles", options });
}

const configs = {
    name: "Fireworks Mask",
    fullScreen: {
        enable: true,
        zIndex: -1,
    },
    background: {
        color: "#000000",
        image: "url('https://particles.js.org/images/background3.jpg')",
        position: "50% 50%",
        repeat: "no-repeat",
        size: "cover"
    },
    backgroundMask: {
        enable: true,
        cover: {
            color: "#000"
        }
    },
    emitters: {
        direction: "top",
        life: {
            count: 0,
            duration: 0.1,
            delay: 0.1
        },
        rate: {
            delay: 0.15,
            quantity: 1
        },
        size: {
            width: 100,
            height: 0
        },
        position: {
            y: 100,
            x: 50
        }
    },
    particles: {
        color: {
            value: "#fff"
        },
        number: {
            value: 0
        },
        destroy: {
            bounds: {
                top: 30
            },
            mode: "split",
            split: {
                count: 1,
                factor: {
                    value: 0.333333
                },
                rate: {
                    value: 100
                },
                particles: {
                    stroke: {
                        width: 0
                    },
                    color: {
                        value: ["#ff595e", "#ffca3a", "#8ac926", "#1982c4", "#6a4c93"]
                    },
                    number: {
                        value: 0
                    },
                    collisions: {
                        enable: false
                    },
                    destroy: {
                        bounds: {
                            top: 0
                        }
                    },
                    opacity: {
                        value: {
                            min: 0.1,
                            max: 1
                        },
                        animation: {
                            enable: true,
                            speed: 0.7,
                            sync: false,
                            startValue: "max",
                            destroy: "min"
                        }
                    },
                    effect: {
                        type: "trail",
                        options: {
                            trail: {
                                length: {
                                    min: 5,
                                    max: 10
                                }
                            }
                        }
                    },
                    shape: {
                        type: "circle"
                    },
                    size: {
                        value: 2,
                        animation: {
                            enable: false
                        }
                    },
                    life: {
                        count: 1,
                        duration: {
                            value: {
                                min: 1,
                                max: 2
                            }
                        }
                    },
                    move: {
                        enable: true,
                        gravity: {
                            enable: true,
                            acceleration: 9.81,
                            inverse: false
                        },
                        decay: 0.1,
                        speed: {
                            min: 10,
                            max: 25
                        },
                        direction: "outside",
                        outModes: "destroy"
                    }
                }
            }
        },
        life: {
            count: 1
        },
        effect: {
            type: "trail",
            options: {
                trail: {
                    length: {
                        min: 10,
                        max: 30
                    },
                    minWidth: 1,
                    maxWidth: 1
                }
            }
        },
        rotate: {
            path: true
        },
        shape: {
            type: "circle"
        },
        size: {
            value: 1
        },
        move: {
            enable: true,
            gravity: {
                acceleration: 15,
                enable: true,
                inverse: true,
                maxSpeed: 100
            },
            speed: {
                min: 10,
                max: 20
            },
            outModes: {
                default: "destroy",
                top: "none"
            }
        }
    },
    sounds: {
        enable: true,
        events: [
            {
                event: "particleRemoved",
                filter: "explodeSoundCheck",
                audio: [
                    "https://particles.js.org/audio/explosion0.mp3",
                    "https://particles.js.org/audio/explosion1.mp3",
                    "https://particles.js.org/audio/explosion2.mp3"
                ]
            }
        ],
        volume: 50
    }
};
loadParticles(configs);
</script>
