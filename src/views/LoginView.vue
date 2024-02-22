<template >
      <div class="bg-gray-100 min-h-screen py-8">

    <template v-if="names.length > 0">
        <ul>
            <li v-for="name in names">
                {{ name.nome }} - <button v-on:click="remove(name)">remove</button>
            </li>
        </ul>
    </template>
    <template v-else>
        Nenhum usuário encontrado!
    </template>
    <form action="" @submit.prevent="login">
        <input type="text" placeholder="email" v-model="email"
            class="rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50">
        <input type="text" placeholder="senha" v-model="senha"
            class="mt-2 rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50">
        <button type="submit"
            class="mt-4 px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 focus:outline-none focus:bg-indigo-700">Login</button>
    </form>
</div>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'

const user = reactive({
    email: "",
    senha: ""
})

const email = ref("");
const senha = ref("");

function login() {
    if (email.value.length === 0 || senha.value.length === 0) {
        alert("Preencha todos os campos");
    } else {
        alert('Login realizado com sucesso: ' + email.value + ' e senha: ' + senha.value);
    }
}

function remove(user) {
    const index = names.findIndex(name => {
        return name.nome === user.nome;
    });
    names.splice(index, 1);
}

const names = reactive([]);

onMounted(() => {
    names.push(
        { nome: "João", idade: 30 },
        { nome: "Rodrigo", idade: 30 }
    );
});
</script>
