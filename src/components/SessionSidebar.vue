<template>
    <small>
        <hr class="th_sparetor">
        <p class="text-white cursor-move font_ text-justify ml-4 h6">
            <span class="text-secondary" :class="iconTitle"></span>
            {{title}}</p>
        <hr class="th_sparetor">

        <input class="form-control form-control-sm" type="text" v-if="showInput" @keyup.13="increment"
               v-model="item_text"/>
        <draggable v-model="items" @group="title" @start="drag=true" @end="drag=false">
            <div v-for="element in items" :key="element" class="item_session text-secondary">
                <a class="font_ text-justify mt-1 ml-4">
                    <span :class="iconItem" class="mb-2 mt-2"></span>
                    <span class="text-white"> {{element}}</span>
                </a>
            </div>
        </draggable>
        <p v-if="!items.length" class="text-secondary font_ text-justify ml-4">Empty list.</p>
        <button class="btn btn-outline-secondary btn-sm mt-1 font_ text-justify ml-4" @click="showForm"
                :disabled="showInput">
            <span class="fa fa-plus"></span> ADD {{title}}
        </button>
        <br class="mb-4">
    </small>
</template>

<script>
    import draggable from 'vuedraggable'

    export default {
        name: 'SessionSidebar',
        components: {
            draggable
        },
        data() {
            return {
                items: [],
                showInput: false,
                item_text: ''
            }
        },
        props: {
            title: String,
            iconTitle: String,
            iconItem: String
        },
        methods: {
            showForm() {
                this.showInput = true
            },
            increment() {
                this.showInput = false
                this.items.push(this.item_text)
                this.item_text = ''
            }
        }
    }
</script>
