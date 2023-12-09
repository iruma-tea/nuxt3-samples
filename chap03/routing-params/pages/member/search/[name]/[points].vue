<template>
    <h1>ルートパラメータ</h1>
    <nav id="breadcrumbs">
        <ul>
            <li>
                <NuxtLink v-bind:to="{name : 'index'}">TOP</NuxtLink>
            </li>
            <li>ルーとパラメータ参照</li>
        </ul>
    </nav>
    <section>
        <p>{{ $route.params }}</p>
    </section>
</template>