<script setup>
import { router } from '@inertiajs/vue3'

defineProps({
    id: String,
    blog: Object
});

const deleteConfirm = (id) => {
    // console.log(id);
    // if (confirm('削除してもよろしいですか？')) {
    //     // 削除処理
    //     Inertia.delete(route('inertia.delete', { id: id }));
    // }

    // 削除処理
    router.delete(`/inertia/${id}`, {
        onBefore: () => confirm('本当に削除しますか？'),
    })  
}
</script>

<template>
    id：{{ id }}
    <br>
    件名：{{ blog.title }}
    <br>
    本文：{{ blog.content }}
    <br>
    <button @click="deleteConfirm(blog.id)">削除</button>
</template>