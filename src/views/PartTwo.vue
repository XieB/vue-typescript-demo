<template>
    <div class="part-two">
        <h1>this is part-two</h1>

        <p>我是data {{message}}</p>
        <p>我是计算属性{{xx}}</p>

        <p @click="onClick">点我</p>
        <Two/>
    </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import Two from "./components/Two.vue";
import {
    Emit,
    Inject,
    Model,
    Prop,
    Provide,
    Watch
} from "vue-property-decorator";
// @Component 修饰符注明了此类为一个 Vue 组件
@Component({
    // 所有的组件选项都可以放在这里
    components: {
        Two
    },
    // props: [
    //     'propB',
    // ]
})
export default class MyComponent extends Vue {
    // 初始数据可以直接声明为实例的属性
    message: string = "Hello!";

    // 组件方法也可以直接声明为实例的方法
    onClick(): void {
        window.alert(this.message);
    }

    created(): void {
        console.log("created");
        setTimeout(() => {
            this.message = "word";
        }, 2000);
    }

    mounted(): void {
        console.log("mounted");
    }

    get xx(): string {
        //计算属性
        return "xx is string";
    }

    @Watch("message") //监听
    messageChanged(): void {
        console.log("message is changed");
    }

    @Prop()
    propA!: number;

    @Prop({ default: "" })
    text!: string;
}
</script>
<style lang="stylus" scoped>
</style>
