<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue' // @/はresources/jsを指すエイリアス  拡張子.vueを書かないとエラーになるので書くこと
import InputLabel from '@/Components/InputLabel.vue'
import TextInput from '@/Components/TextInput.vue'
import { ref } from 'vue';

const inputValue = ref(''); // 入力値を管理するref
</script>

<template>
<GuestLayout>
    <InputLabel value="件名">タイトル</InputLabel>
    <TextInput modelValue="初期値が入ります" v-model="inputValue"></TextInput>
    <p>入力された値: {{ inputValue }}</p>
</GuestLayout>
</template>