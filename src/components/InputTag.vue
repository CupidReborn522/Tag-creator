<script>

export default {
    emits: ["onTagsChange"],
    data() {
        return {
            currentValue: "",
            tags: [],

        }

    },
    methods: {
        handleKeydown(e) {
            if (e.key == 'Backspace' && this.currentValue == '' && this.tags.length > 0) {
                this.tags.pop();
                this.$emit('onTagsChange', this.tags);
            }
        },
        handleSubmit() {
            const exist = this.tags.some(item => item == this.currentValue)
            if (this.currentValue != '' && !exist) {
                this.tags.push(this.currentValue);
                this.currentValue = '';
                this.$emit('onTagsChange', this.tags);
                // console.log(this.tags)
            }
        },

        deleteTag(tag) {
            this.tags = this.tags.filter(item => item != tag);
            this.$emit('onTagsChange', this.tags);
        }
    }
}

</script>

<template>
    <div class="inputTag">
        <div class="tags">
            <div class="tag" style="opacity: 0;" v-if="tags.length == 0">
                <button @click="deleteTag(tag)" style="opacity: 0; pointer-events: none;">X</button>
            </div>
            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }}
                <button @click="deleteTag(tag)">X</button>
            </div>
        </div>
        <form @submit.prevent="handleSubmit">
            <input maxlength="20" type="text" name="text" id="tagText" v-model="currentValue" @keydown="handleKeydown">
        </form>
    </div>
</template>

<style scoped>
.inputTag {
    display: inline-flex;
    border: 1px solid black;
    border-radius: 3px;
}

.inputTag form {
    display: inline-flex;
}

.tag button {
    background-color: transparent;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.tag button:hover {
    background-color: #ccc;
}

.tags {
    display: flex;
    gap: 3px;
    padding: 3px;
}

.tags .tag {
    display: flex;
    padding: 5px;
    border: 1px solid rgb(100, 100, 100);
    gap: 5px;
    align-content: center;
    align-items: center;
    border-radius: 3px;
}

#tagText {
    border: none;
    outline: none;
    padding: 0 5px;
}
</style>