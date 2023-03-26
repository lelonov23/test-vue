<script>
import AddWatch from "../components/AddWatch.vue"
import { defineAsyncComponent, defineComponent, ref } from "vue"
export default defineComponent({
    components: {
    Stopwatch: defineAsyncComponent(() => import("../components/Stopwatch.vue")),
    AddWatch
},
    setup() {
        const watches = ref([])

        const addStopwatch = () => {
            watches.value.push('Stopwatch')
        }
        return {
            addStopwatch,
            watches        
        }
    },
})
</script>

<template>
    <div class="contain">
        <div v-for="child in watches" class="child">
            <component :is="child"></component>
        </div>
        <AddWatch @add="addStopwatch()"/>
    </div>
</template>

<style scoped>
.contain {
    display: flex;
    flex-wrap: wrap;
    justify-content: left;
    max-width: 775px;
    gap: 50px;
    margin: 50px auto 0 auto;
}
@media only screen and (max-width: 790px) {
    .containerr {
        max-width: 500px;
    }
}

@media only screen and (max-width: 516px) {
    .containerr {
        max-width: 225px;
    }
}
.child {
    flex-basis: 120px;
    position: relative;
}
</style>