<template>
    <input ref="inputElement" v-model="toDoTask" autofocus placeholder="Task" @keyup.enter="addToDo"/>
    <button @click=addToDo>+</button>
    <div id="list">
        <a>{{toDoList}}</a>
    </div>
    <br>
    <div v-for="task in toDoList">
        <li v-if="!task.done">
            <span>
                {{task.id}}
                {{task.title}} 
                <button @click="finishTask(task.id)">finish</button>
            </span>
        </li>
    </div>
</template>

<script>
    import {ref, onMounted} from 'vue'
    const toDoTask = ref('')
    let toDoList = ref([])
    const inputElement = ref(null)
    
    export default{
        setup(){
            toDoList = []

            const addToDo = () => 
            {
                if(toDoTask.value === 0 | toDoTask.value === '')
                {
                    inputElement.value.focus()
                    return
                }
                let task = {
                    "id" : toDoList.length + 1,
                    "title" : toDoTask.value,
                    "done" : false
                }
                toDoList.push(task)
                toDoTask.value = ''
                inputElement.value.focus()
            }

            onMounted (()=>{
                toDoTask.value = ''
            })

            const finishTask = (taskId) => {
                // Use toDoList.value to access the reactive array
                const index = toDoList.value.findIndex(task => task.id === taskId);
                if (index !== -1) {
                    // Correctly reference toDoList.value[index] when creating updatedTask
                    const updatedTask = { ...toDoList.value[index], done: true };
                    // Correctly use toDoList.value for splice operation
                    toDoList.value.splice(index, 1, updatedTask); // Replace the task with its updated copy
                } else {
                    console.error('Task not found:', taskId);
                }
            };
            return {finishTask, addToDo, toDoList, toDoTask, inputElement}
        }
    }
</script>