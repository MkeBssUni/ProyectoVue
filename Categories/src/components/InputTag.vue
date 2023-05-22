<script>
export default{
    //props: ["onTagsChange"],
    emits: ["onTagsChange"],
    data(){
        return{
            currentValue: ' ',
            tags: [],
        };
    },
    methods:{
        handleKeyDown(e){
            if(e.key == 'Backspace' && this.currentValue !== ' '){
                this.tags.pop()
                //this.onTagsChange(this.tags)
                this.$emit("onTagsChange")
            }
        },
        handleSubmit(){
            if(this.currentValue!==' '){
                const exists = this.tags.some((item)=> item == this.currentValue.toUpperCase())
                if(!exists){
                    this.tags.push(this.currentValue.toUpperCase())
                    //this.onTagsChange(this.tags)
                    this.$emit("onTagsChange")
                    this.currentValue= ''
                }else{
                    alert("Tag ya existente")
                    this.currentValue= ''
                }
            }
        },
        deleteTag(tag){
            this.tags = this.tags.filter((item) => item !== tag )
            //this.onTagsChange(this.tags)
            this.$emit("onTagsChange")
        }
    }
}
</script>

<template>
    <div class="InputTag">
        <div class="tags">
            <div class="tag" v-for="(tag,index) in tags" :key="index">{{ tag }}
                <button @click="deleteTag(tag)">x</button>
            </div>
            
        </div>
        <form @submit.prevent="handleSubmit">
            <input class="input" type="text" v-model="currentValue" @keydown="handleKeyDown"  />
        </form>
    </div>
</template>

<style scoped>
.inputTag{
    display: inline-flex;
    border: solid 1px #000;
    border-radius: 3px;
}

.tags{
    display: flex;
    gap: 3px;
    padding: 5px;
}
.tags .tag{
    display: flex;
    padding: 5px;
    border: solid 1px #ccc;
    gap: 5px;
    align-content: center;
    border-radius: 3px;
}

.inputTag .input{
    border: none;
    outline: none;
    padding: 0.5px;
}

.inputTag form{
    display: inline-flex;
}

.tag button{
    background-color: transparent;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.tag button:hoover{
    background-color: #2c2c2c;
}

</style>