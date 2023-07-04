<template>
    <div class="note-item">
        <div class="id-content">
            <span>{{ noteItem.id }}</span>
        </div>
        <div class="note-content"> {{ noteItem.note }}
        </div> 
    </div>
</template>

<script>
export default {
    props : {
        noteItem : {
            type : Object,
            required : true
        }
    }
}
</script>