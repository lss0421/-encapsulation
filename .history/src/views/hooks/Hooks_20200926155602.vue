<template>
<div class="box">
    <div class="fz-20">鼠标移动坐标</div>
    <div>{{ x }} --- {{ y }}</div>
    <div class="fz-20">时间</div>
    <div>{{ date._value }}</div>
    <div class="fz-20">本地存储</div>
    <div class="flex">
        <a-button type="danger" ghost @click="setMessage('user', name)">
            储存localStorage
        </a-button>
        <a-button type="danger" ghost @click="clearMessage('user')">
            清除localStorage
        </a-button>

        <a-button type="danger" ghost @click="getMessage">
            sessionStorage同理
        </a-button>
    </div>
</div>
</template>

<script lang="ts">
import {
    defineComponent,
    reactive,
    toRefs,
    SetupContext
} from "vue";
import {
    useMouse
} from "@/components/hooks/useMouse";
import {
    useTime
} from "@/components/hooks/useTime";
import {
    usStorage
} from "@/components/hooks/useStorage";
interface Data {
    username: string;
    name: any;
}
export default defineComponent({
    name: "",
    props: {},
    components: {
        //  countdown
    },
    setup(props, ctx: SetupContext) {
        const {
            x,
            y
        } = useMouse();
        const {
            date
        } = useTime();
        const {
            getMessage,
            setMessage,
            clearMessage
        } = usStorage();
        const data: Data = reactive < Data > ({
            username: "",
            name: "133131321",
        });
        return {
            ...toRefs(data),
            x,
            y,
            date,
            getMessage,
            setMessage,
            clearMessage,
        };
    },
});
</script>

<style lang="scss" scoped>
.box {
    padding: 30px;
}
</style>
