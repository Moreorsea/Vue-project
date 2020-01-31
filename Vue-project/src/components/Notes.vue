<template>
    <!--note list-->
	<div class="notes">
       <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index">
         <div class="note-header" :class="{full: !grid}">
           <p>{{ note.title }}</p>
           <p style="cursor: pointer;" @click="removeNote(index)">x</p>
        </div>
        <div class="note-body" :class="note.priority">
           <p>{{ note.descr }}</p>
           <span> {{ note.date }} </span>
         </div>
        </div>
	</div>
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            required: true
        },
        grid: {
            type: Boolean,
            required: true
        }
    },
    methods: {
        removeNote (index) {
            this.$emit('remove', index)
        }
    }
}
</script>

<style lang="scss">
.notes {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}

.note {
    width: 48%;
    &.full {
        width: 100%;
    }

    &.full .note-body {
        text-align: center;
    }
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: #ffffff;
    transition: all .25s cubic-bezier(.02,.01,.47,1);
    box-shadow: 0 30px 30px rgba(0,0,0,.02);
    &:hover {
        box-shadow: 0 30px 30px rgba(0,0,0,.04);
        transform: translate(0,-6px);
        transition-delay: 0s !important;
    }
    
}

.note-body {
    p {
        margin: 20px 0;
    }
    span {
        font-size: 14px;
        color: #999999;
    }
    &.important {
        background-color: yellow;
    }
    &.critical {
        background-color: red;
    }
    
}

.note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1 {
        font-size: 32px;
    }
    p {
        color: #402caf;
        font-size: 22px;
    }
    svg {
        margin-right: 12px;
        color: #999999; 
        &.active {
            color: #402caf;
        }
        &:last-child {
            margin-right: 0px;
        }
    }
    &.full {
        justify-content: center;
        p {
            margin-right: 16px;
            text-align: center;
            &:last-child {
                margin-right: 0;
            }
        }
    }
}

</style>