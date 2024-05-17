<script setup>

    import { ref } from 'vue';

    const items = ref([
    {
        title: "Tema 1",
        subtitle: "Texto del tema 1",
        estado: false, // Inicialmente, todos los subtítulos están ocultos
    },
    {
        title: "Tema 2",
        subtitle: "Texto del tema 2",
        estado: false,
    },
    {
        title: "Tema 3",
        subtitle: "Texto del tema 3",
        estado: false,
    }
]);

function mostrar(index) {
    // Cambiar el estado del elemento seleccionado
    items.value[index].estado = !items.value[index].estado;
    // Ocultar los otros elementos
    for (let i = 0; i < items.value.length; i++) {
        if (i !== index) {
            items.value[i].estado = false;
        }
    }
}


</script>

<template>

<div class="flex mt-12 ">
    <!-- Bloque #1 -->
    <div class="bg-blue-400 w-2/5 ml-[5%]">
        <div>
            <div class="mb-1 py-1 px-3 text-xl " v-for="(item, i) in items" :key="i">
                    <div class=" bg-blue-200 mt-2 mb-1 px-2 py-1 justify-between flex" :class='{"bg-slate-500 text-white" : item.estado}' ">
                        {{ item.title }}    
                        <span class="text-2xl cursor-pointer" @click="mostrar(i)">{{ item.estado ? '-' : '+' }}</span>
                    </div>  
                <div v-show="item.estado" class="bg-slate-100 px-2 mt-2 py-1 h-24">{{ item.subtitle }}</div>
            </div>
        </div>
    </div>
</div>


</template>