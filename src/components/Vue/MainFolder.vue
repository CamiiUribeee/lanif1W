<script setup>

    import {ref} from 'vue'
    import data from '../data.json'
    import ArrowRight from '../Vue/Icons/ArrowRight.vue'
    import ArrowDown from '../Vue/Icons/ArrowDown.vue'
    import Folder from '../Vue/Icons/Folder.vue'


    import Folders from '../Vue/Folders.vue'

    let folders = ref(data)
    let hide = ref(true)

    let amountOfFolders = 0
    for (const key in data) {
        amountOfFolders += 1
    }

    let foldersArray = ref(new Array(amountOfFolders).fill(false))

    function display(index) {
        foldersArray.value[index] = !foldersArray.value[index]
        console.log(foldersArray)
    }







</script>

<template>
    <section class="max-w-6xl w-full mx-auto flex flex-col justify-start items-start">
        <section class="" v-for="(folder, index) in folders" :key="index">
            
            <section class="p-3 flex flex-row justify-start items-center gap-2 hover:bg-slate-100">
                <button @click="display(index)" class="w-6 h-6 flex justify-center items-center hover:text-blue-400">
                    <ArrowRight v-if="foldersArray[index] == false"></ArrowRight>
                    <ArrowDown v-if="foldersArray[index]"></ArrowDown>
                </button>
                <div class="flex flex-row justify-start items-center gap-1 w-[36rem]" @dblclick="display(index)">
                    <Folder class="text-yellow-400"></Folder>
                    <h1>{{ folder.name }}</h1>                
                </div>
            </section>

            <Folders v-if="folder.files && foldersArray[index]" :information="folder.files"></Folders>
            <!-- <section v-if="folder.files && foldersArray[index]" class="py-1 flex flex-row justify-start items-center gap-2 hover:bg-slate-100">
                Hola
            </section> -->
            
            
        </section>
    </section>
</template>