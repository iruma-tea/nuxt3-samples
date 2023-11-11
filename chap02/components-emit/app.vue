<script setup lang="ts">
// 会員リストデータを用意
const memberListInit = new Map<number, Member>();
memberListInit.set(33456, {id: 22456, name: "田中太郎", email: "bow@example.com", points: 35, note: "初回特典あり。"});
memberListInit.set(47783, {id: 47783, name: "鈴木二郎", email: "mue@example.com", points: 53});
const memberList = ref(memberListInit);

// 会員リスト内の会員のポイント合計
const totalPoints = computed(
  (): number => {
    let total = 0;
    for (const member of memberList.value.values()) {
      total += member.points;
    }
    return total;
  }
);

//Emitにより実行されるメソッド。
const onIncrementPoint = (id: number): void => {
  const member = memberList.value.get(id);
  if (member != undefined) {
    member.points++;
  }
}

interface Member {
  id: number;
  name: string;
  email: string;
  points: number;
  note?: string;
}
</script>

<template>
  <section>
    <h1>会員リスト</h1>
    <p>全会員の保有ポイントの合計: {{ totalPoints }}</p>
    <OneMember 
      v-for="[id, member] in memberList"
      v-bind:key="id"
      v-bind:id="id"
      v-bind:name="member.name"
      v-bind:email="member.email"
      v-bind:points="member.points"
      v-bind:note="member.note"
      v-on:increment-point="onIncrementPoint"
    />
  </section>
</template>
