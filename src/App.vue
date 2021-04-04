<template>
    <div>
        <div class="custom-made">
            <div>
                <transition name="rotate" mode="out-in">
                    <component :is="mode" @watchOut="watchingOut($event)" @confirmed="mode = 'app-question'"></component>
                </transition>
            </div>
        </div>
    </div>
</template>

<script>
    import Question from './components/Question.vue';
    import Answer from './components/Answer.vue';

    export default {
        data() {
            return {
                mode: 'app-question'
            }
        },
        methods: {
          answered(isCorrect) {
              if (isCorrect) {
                  this.mode = 'app-answer';
              } else {
                  this.mode = 'app-question';
                  alert('Wrong, try again!');
              }
          },
          watchingOut() {
              this.mode = 'app-answer';
          }
        },
        components: {
            appQuestion: Question,
            appAnswer: Answer
        }
    }
</script>
<style>
    .rotate-enter {
        /* transform: rotateY(0deg); */
    }
    .rotate-enter-active {
        animation: rotate-in 0.5s ease-out forwards;
    }
    .rotate-leave {
        /* transform: rotateY(0deg); */
    }
    .rotate-leave-active {
        animation: rotate-out 0.5s ease-out forwards;
    }
    @keyframes rotate-out {
        from {
            transform: rotateY(0deg);
        }
        to {
            transform: rotateY(90deg);
        }
    }
    @keyframes rotate-in {
        from {
            transform: rotateY(90deg);
        }
        to {
            transform: rotateY(0deg);
        }
    }
    .custom-made {
        position: absolute;
        top: 50%;
        transform: translate(-50%, -50%);
        left: 50%;
    }
</style>


