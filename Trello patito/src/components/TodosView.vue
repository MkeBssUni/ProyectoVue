<script setup>
import { onMounted, ref, reactive } from "vue";
import InputNew from "./InputNew.vue";

const count = ref(0);
let boards = reactive([
    {
        id: crypto.randomUUID(),
        name: 'Pendientes',
        items: [
            {
                id: crypto.randomUUID(),
                title: 'Revisión de DFR'
            },
            {
                id: crypto.randomUUID(),
                title: 'Corrección de DFR'
            },
        ],
    }, {

        id: crypto.randomUUID(),
        name: 'En proceso',
        items: [
            {
                id: crypto.randomUUID(),
                title: 'Capacitación autonoma'
            },
            {
                id: crypto.randomUUID(),
                title: 'Debugear el código'
            },
        ],
    }
]);

function handleNewItem(text, board) {
    console.log(text.value, board.name)
    board.items.push({
        id: crypto.randomUUID,
        title: text.value
    })
}

function hanldeNewBoard() {
    const name = prompt('Nombre del tablero');
    if (name) {
        const board = {
            id: crypto.randomUUID(),
            name: name,
            items: [],
        };

        boards.push(board);
    }
}
</script>

<template>
    <div>
        <nav>
            <ul>
                <li><a href="#" @click="hanldeNewBoard">Crear tablero</a></li>
            </ul>
        </nav>
        <div class="boards-container">
            <div class="boards">
                <div class="board" v-for="board in boards" :key="board.id">
                    <div>{{ board.name }}</div>
                    <InputNew @on-new-item="(text) => handleNewItem(text, board)" />
                    <div class="items">
                        <div class="item" v-for="item in board.items" :key="item.id">
                            <div>{{ item.title }}</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped> /* Scoped es para que los estilos únicamente se apliquen a los componentes del archivo y no de forma global */
 .drop-zone {
     background-color: #eee;
     margin-bottom: 10px;
     padding: 10px;
 }

 .drag-el {
     background-color: #fff;
     margin-bottom: 10px;
     padding: 5px;
 }

 .boards {
     display: flex;
     gap: 10px;
 }

 .board {
     background: #ccc;
     padding: 10px;
 }
</style>