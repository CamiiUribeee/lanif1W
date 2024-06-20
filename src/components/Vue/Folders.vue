<script setup>

    import {ref} from 'vue'
    import ArrowRight from '../Vue/Icons/ArrowRight.vue'
    import ArrowDown from '../Vue/Icons/ArrowDown.vue'
    import Folder from '../Vue/Icons/Folder.vue'
    import File from '../Vue/Icons/File.vue'

    let props = defineProps({
        information: Array
    })

    let amountOfFolders = 0
    for (const key in props.information) {
        amountOfFolders += 1
    }

    let foldersArray = ref(new Array(amountOfFolders).fill(false))


    let displaying = ref(false)

    function display(index) {
        foldersArray.value[index] = ! foldersArray.value[index]
    }



</script>

<template>
    <section v-for="(file, index) in props.information" :key="index" class="ml-8">
        <section v-if="file.name" class="p-3 flex flex-row justify-start items-center gap-2 hover:bg-slate-100">
            <button @click="display(index)" class="w-6 h-6 flex justify-center items-center hover:text-blue-400" v-if="file.files">
                <ArrowRight v-if="file.files && foldersArray[index] == false"></ArrowRight>
                <ArrowDown v-if="file.files && foldersArray[index]"></ArrowDown>
            </button>
            <div class="flex flex-row justify-start items-center gap-1 w-96" @dblclick="display(index)">
                <Folder v-if="file.files" class="text-yellow-400"></Folder>
                <File v-if="!file.files" class="text-blue-400"></File>
                <h1>{{ file.name }}</h1>
            </div>

            
            
        </section>
        <h1 v-if="file.files && foldersArray[index]">
            <Folders :information="file.files"></Folders>
        </h1>        
    </section>
</template>