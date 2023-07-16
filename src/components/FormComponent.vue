<template>
    <div class="box">
        <div class="columns">
            <!-- is * corresponde a 8 colunas -->
            <div class="column is-8" role="form" aria-label="Create a new task form.">
                <input type="text" class="input" placeholder="Which task do you want to start?">
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <section>
                        <strong>
                            {{ elapsedTime }}
                        </strong>
                    </section>
                    <button class="button" @click="start">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finish">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'FormComponent',
    data () {
        return {
            timeSecond: 0,
            stopwatch: 0
        }
    },
    computed: {
        elapsedTime () : string {
            return new Date(this.timeSecond * 1000).toISOString().substring(11,19)
        }
    },
    methods: {
        start() {
            // comecar a contagem do timeSecond / 1 seg = 1000ms
            this.stopwatch = setInterval(() => {
                this.timeSecond += 1
            }, 1000)
            
        },
        finish() {
            clearInterval(this.stopwatch)
        }
    }
})
</script>