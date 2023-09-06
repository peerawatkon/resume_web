<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";
import { useRouter } from "vue-router";
let name = ref(''), 
    price = ref(0), 
    routerName = ref(''), 
    _id = ref('');
const router = useRouter()
onMounted(() => {
    routerName.value = router.currentRoute.value.name;
    _id.value = router.currentRoute.value.params?.id;
    console.log("routerName", routerName.value);
    console.log("_id", _id.value);
    if(routerName.value == "edit") {
        initEdit();
    }
});
const API_PATH = import.meta.env.VITE_API_PATH;
const initEdit = async () => {
    const {data} = await axios.get(`${API_PATH}/getproduct/${_id.value}`);
    name.value = data.data.name;
    price.value = data.data.price;
}
const submit = async () => {
    const req = {
        name:name.value, price:price.value
    };
    if(routerName.value == "create" ) {
        await axios.post(
          `${API_PATH}/create`,
            req
        ).then((response) => {
            name.value = '';
            price.value = '';
        });
    } else {
        await axios.post(
            `${API_PATH}/update/${_id.value}`,
            req
        ).then((response) => {
            router.push({name : 'home', replace: true});
        });
    }
 };

</script>

<template>
  <div className="card w-96 bg-base-100 shadow-xl">
    <figure>
      <img src="../../public/images/55.jpg" alt="fruit" />
    </figure>
    <div className="card-body">
      <h2 className="card-title">fruit</h2>
      <div className="card-actions justify-end">
        <p>Please add product?</p>
        <input
          type="text"
          placeholder="Name"
          class="input input-bordered w-full max-w-md mr-5"
          v-model="name"
        />
        <input
          type="number"
          placeholder="Price"
          class="input input-bordered w-full max-w-md mr-5"
          v-model="price"
        />
        <button class="btn btn-neutral" v-on:click="submit()">create</button>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
