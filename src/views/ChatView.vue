<script setup>
import { onMounted, ref} from 'vue';
import {
    app,
    auth,
    database,
    ref as refDb,
    set,
    push
} from '../firebaseConfig'
let chat = ref("");
const studentId = "รหัสนักศึกษา"
const onSend = () => {
    push(refDb(database,'all_chat/group_1/'),{
        "user": studentId,
        "message": chat.value,
        "dataTime": new Date().toISOString()
    });
    chat.value = "";
}

// onMounted(() => {
//     push(refDb(database, 'test'), {
//         "6314110023": "Hello World"
//     });
// });
</script>


<template>
    <div class="flex">
        <div class="overflow-y-scroll bg-white h-[90vh] w-[30%]">
            <div class="w-full bg-[#DCA3FF] h-36 border-black-700 border-4" v-for="i in 100" :key="i">

            </div>
        </div>
        <div class="bg-gray-50 h-[90vh] w-[70%]">
            <div class="overflow-y-scroll h-[90%]">
                <div className="chat chat-start">
                    <div className="chat-bubble">私の名前はケッセンです,<br />22才.</div>
                </div>
                <div className="chat chat-end">
                    <div className="chat-bubble">私はあなたに会えてうれしいです!</div>
                </div>
            </div>
            <div class="flex h-[10%] gap-4">
                <input v-on:keyup.enter="onSend" v-model="chat" type="text" placeholder="Type here" class="input input-bordered w-[80%] h-full" />
                <button @Click = "onSend" class="w-[20%] btn h-full ">Send</button>
            </div>
        </div>
    </div>
</template>
<style scoped></style>
