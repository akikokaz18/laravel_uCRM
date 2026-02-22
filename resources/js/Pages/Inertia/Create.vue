<script setup>
import { reactive } from 'vue';
// import { Inertia } '@inertiajs/inertia'; // この書き方でInertiaをimportできない
import { router } from '@inertiajs/vue3';
import BreezeValidationErrors from '@/Components/ValidationErrors.vue'

defineProps({
    errors: Object
});

const form = reactive({
    title: null,
    content: null
});

const submitFunction = () => {
    // Inertia.post('inertia', form);
    // router.post('inertia', form); // POST http://localhost:8000/inertia/inertia 404 (Not Found) になる
    router.post(route('inertia.store'), form); // http://localhost:8000/inertia/index へ遷移した。これでOK。
}

</script>

<template>
    <BreezeValidationErrors :errors="errors" />
    <form @submit.prevent="submitFunction">
        <input type="text" name="title" v-model="form.title"><br>
        <div v-if="errors.title" class="text-red-500">{{ errors.title }}</div>
        <input type="text" name="content" v-model="form.content"><br>
        <div v-if="errors.content" class="text-red-500">{{ errors.content }}</div>
        <button>送信</button>
    </form>

</template>