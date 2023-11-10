<script setup lang="ts">
// propsインタフェース
interface Props {
    id: number;
    name: string;
    email: string;
    points: number;
    note?: string;
}
// propsオブジェクトの設定。
const props = defineProps<Props>();

// このコンポーネント内で利用するポイント数のテンプレート変数。
const localPoints = ref(props.points);
// Propsのnoteを加工する算出するプロパティ
const localNote = computed(
    ():string => {
        let localNote = props.note;
        if (localNote == undefined) {
            localNote = "--";
        }
        return localNote;
    }
);
// ポイント加算ボタンをクリックしたとこのメソッド
const pointUp = ():void => {
    localPoints.value++;
};
</script>
<template>
    <section class="box">
        <h4>{{ name }}さんの権限</h4>
        <dl>
            <dt>ID</dt>
            <dd>{{ id }}</dd>
            <dt>メールアドレス</dt>
            <dd>{{ email }}</dd>
            <dt>保有ポイント</dt>
            <dd>{{ localPoints }}</dd>
            <dt>備考</dt>
            <dd>{{ localNote }}</dd>
        </dl>
        <button v-on:click="pointUp">ポイント加算</button>
    </section>
</template>
<style scoped>
.box {
    border: green 1px solid;
    margin: 10px;
}
</style>