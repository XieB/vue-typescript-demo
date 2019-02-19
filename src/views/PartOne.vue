<template>
    <div class="part-one">
        <h1>this is part-one</h1>
        <p>{{data}}</p>
        <One />
    </div>
</template>

<script lang="ts">
import Vue, { VNode } from "vue";
import One from './components/One.vue';

export default Vue.extend({
    components: {
        One
    },
    data() {
        return {
            data: "part-one"
        };
    },
    created() {
        this.hello();
    },
    mounted() {
        console.log("this is mounted");
    },
    methods: {
        hello(): void {
            setTimeout(() => {
                this.data = "hello";
            }, 2000);
        }
    },

    computed: {
        word(): string {
            return "word";
        }
    },

    render(createElement): VNode {
        return createElement("div", this.word);
    }
});
</script>
<style lang="stylus" scoped>

</style>
