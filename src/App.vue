<template>
    <div class="">
        <div
            class="container w-full min-h-screen flex flex-col justify-center items-center mx-auto text-center p-8 button-lg"
        >
            <h1 v-if="!isAccepted" class="md:text-4xl text-lg font-bold mb-4 md:ml-36 ml-0">
                Will you be my Valentine?
            </h1>
            <div
                v-if="!isAccepted"
                :class="{ 'flex-col': !isAccepted, 'md:flex-row': !isAccepted }"
                class="flex gap-4 mt-3"
            >
                <button
                    class="text-white text-2xl font-bold py-2 px-6 md:px-14 rounded-md mb-2 md:mb-0 bg-teal-400"
                    @click="accepted"
                >
                    Yes
                </button>
                <button
                    class="bg-red-500 hover:bg-red-600 text-white text-2xl font-bold py-2 px-6 md:px-14 rounded-md btn-lg md:self-start"
                    @mouseover="moveButton"
                    @touchstart="moveButton"
                >
                    {{ buttonText }}
                </button>
            </div>
            <div
                v-if="isAccepted"
                class="flex mt-4 w-full md:w-1/2 justify-center items-center shadow-md shadow-white md:h-96 aspect-ratio-16/9 overflow-hidden rounded-lg"
            >
                <img class="p-2 w-full h-full object-cover" src="/src/assets/va.gif" alt="" />
            </div>
        </div>
        <footer
            class="flex justify-center text-center font-mono font-bold text-md text-gray-200 bottom-0 mt-8 shadow-md p-4 w-full bg-gray-800"
        >
            <div class="flex flex-col">
                <div>
                    Made with Vue
                    <img
                        class="w-4 aspect-ratio-2/3 h-4 inline-block relative bottom-1 mt-2"
                        src="../public/favicon.ico"
                        alt=""
                    />
                    and TailwindCSS
                    <img
                        class="w-4 aspect-ratio-2/3 h-4 inline-block relative bottom-1 mt-1"
                        src="/src/assets/tailwind.png"
                        alt=""
                    />
                </div>
                <span class="text-md font-mono mt-1">&copy; 2024 Walelgn Dagne </span>
            </div>
        </footer>
    </div>
</template>

<script>
export default {
    data() {
        return {
            buttonText: 'No',
            isAccepted: false,
        }
    },
    methods: {
        accepted() {
            this.isAccepted = true
            // this.moveButton()
        },
        moveButton() {
            if (this.isAccepted) {
                const btn = document.querySelector('.btn-lg')
                btn.style.left = '55%'
                btn.style.top = ''
                btn.style.transition = '0.5s'
                this.buttonText = 'No'
                return
            }

            const btn = document.querySelector('.btn-lg')
            const btnWidth = btn.offsetWidth
            const btnHeight = btn.offsetHeight
            const height = window.innerHeight - btnHeight
            const width = window.innerWidth - btnWidth
            const newHeight = Math.floor(Math.random() * height)
            const newWidth = Math.floor(Math.random() * width)
            btn.style.left = `${newWidth}px`
            btn.style.top = `${newHeight}px`
            btn.style.transition = '0.5s'
            this.buttonText = 'Say Yes!'
        },
        changeButtonText() {
            const texts = [
                'You clicked by mistake!',
                'Did you mean yes?',
                'Are you sure?',
                'You are stubborn!',
                'I am stubborn too',
                'Last chance',
                'You have to say yes',
                'I can do this all day!!',
            ]
            const index = texts.indexOf(this.buttonText)
            if (index === texts.length - 1) {
                this.buttonText = texts[0]
                return
            }
            this.buttonText = texts[index + 1]
        },
    },
}
</script>

<style>
body {
    background: rgb(131, 58, 180);
    background: linear-gradient(90deg, rgba(131, 58, 180, 1) 0%, rgba(237, 94, 94, 1) 100%, rgba(252, 176, 69, 1) 100%);
}

.btn-lg {
    position: absolute;
    transition: 0.5s;
    gap: 0.5rem;
    left: 55%;
}
@media (max-width: 768px) {
    .click-me {
        display: flex;
        flex-direction: column;
        left: 65%;
    }
}
</style>
