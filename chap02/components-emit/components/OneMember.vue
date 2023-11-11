<script setup lang="ts">
interface Props {
    id: number;
    name: string;
    email: string;
    points: number;
    note?: string;
}

// Emits型を定義
type Emits = {
    incrementPoint: [id: number];
};
</script>
<template>

</template>
<style scoped>
.box {
    border: green 1px solid;
    margin: 10px;
}
</style>