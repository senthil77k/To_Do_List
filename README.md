# Ex03 To-Do List using JavaScript
## Date:23-03-2025

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-do List</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,100..900;1,100..900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
    <script src="index.js" defer></script>
</head>
<body>
    <h1 class="title">To-Do List</h1>
    
    <div class="all-tasks">
        <h2 class="task-list-title">My lists</h2>
        <ul class="task-list" data-lists>
            <!-- <li class="active-list"> Youtube </li>
            <li class="list-name">Work</li>
            <li class="list-name">Grocery</li> -->
        </ul>
        <form action="" data-new-list-form>
            <input type="text" class="new list" data-new-list-input placeholder="new list name" aria-label="new list name">
            <button class="btn create" aria-label="create new list">+</button>
        </form>
    </div>
    <div class="todo-list" data-list-display-container>
        <div class="todo-header">
            <h2 class="list-title" data-list-title>List Name</h2>
            <p class="task-count" data-list-count></p>
        </div>
        <div class="todo-body">
            <div class="tasks" data-tasks>
                
            </div>
            <div class="new-task-creator">
                <form action="" data-new-task-form>
                    <input type="text" data-new-task-input class="new task" placeholder="new task name" aria-label="new task name">
                    <button class="btn create tasks" aria-label="create new task">+</button>
                </form>
            </div>
            <div class="delete-stuff">
                <button class="btn delete" data-clear-complete-tasks-button>Clear completed tasks</button>
                <button class="btn delete" data-delete-list-button>Delete list</button>
            </div>
            <div>
                <p style="color: rgb(21, 21, 21);">Created by senthil kumaran</p>
            </div>
        </div>
    </div>
    <template id="task-template">
        <div class="task">
            <input type="checkbox">
            <label><span class="custom-checkbox"></span></label>
        </div>
    </template>
    
</body>
</html>
```
CSS
```
:root {
    --clr-primary: #000;
    --clr-light: #f4f4f4;
    --clr-dark: #333;
    --clr-warning: rgb(99, 36, 36);
}

*, *::before, *::after {
    font-family: inherit;
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: "Work Sans", sans-serif;
    font-weight: 300;
    font-size: 1.5rem;
    background-color: var(--clr-primary);
    color: var(--clr-light);
    display: grid;
    grid:
        "header header header header" auto
        ". lists active ." auto /
        1fr minmax(100px, 300px) minmax(250px, 500px) 1fr;
}

.title {
    grid-area: header;
    text-align: center;
    font-size: calc(7vw + 2rem);
    font-weight: 900;
    color: rgba();
    letter-spacing: 2px;
}

.all-tasks {
    grid-area: lists;
}

.task-list {
    font-size: 1.2rem;
    line-height: 1.7;
    list-style: circle;
    padding-left: 1.1em;
}

.list-name {
    cursor: pointer;
}

.list-name:hover, .list-name:focus {
    opacity: 0.7;
}

form {
    display: flex;
}

.btn {
    background: transparent;
    cursor: pointer;
    border: 0;
    padding: 0;
    color: var(--clr-light);
}

.btn.create {
    font-size: 1.5rem;
    font-weight: 700;
    margin-right: 0.25em;
    transition: opacity 250ms ease-in;
}

.btn.create:hover, .btn.list:focus {
    opacity: .5;
}

.new {
    background: transparent;
    border: 0;
    color: inherit;
    border-bottom: 1px solid currentColor; /* current color reflects the color property */
    font-size: inherit;
    outline: none;
    order: 2;
}

.new::placeholder {
    color: var(--clr-light);
    opacity: .5;
}

.new:focus::placeholder {
    opacity: .2;
}

.new.list {
    font-size: 1.2rem;
    padding: 0.25em;
}

.new.task {
    margin-bottom: 0;
    padding: 0.25em;
}

.active-list {
    font-weight: 700;
    letter-spacing: 1px;
    cursor: pointer;
}

.todo-list {
    --spacer: 2rem;

    grid-area: active;
    background: var(--clr-light);
    color: var(--clr-dark);
}

.todo-header {
    padding: var(--spacer);
    background: hsla(0, 0%, 50%, 0.25);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.list-title {
    margin: 0 1em 0 0;
}

.task-count {
    margin: 0;
    font-size: 1rem;
}

.todo-body {
    padding: var(--spacer);
    position: relative;
}

.new.task::placeholder {
    color: var(--clr-dark);
}

.btn.tasks {
    color: var(--clr-dark);
}

[type="checkbox"] {
    opacity: 0;
    position: absolute;
}

.task label {
    display: inline-flex;
    align-items: center;
    position: relative;
}

.task {
    position: relative;
    margin-bottom: 1.25em;
}

.task::after {
    content: "";
    position: absolute;
    right: 0;
    left: 0;
    bottom: -0.5em;
    height: 1px;
    background: currentColor;
    opacity: .2;
}

.custom-checkbox {
    --size: 0.75em;

    display: inline-block;
    width: var(--size);
    height: var(--size);
    cursor: pointer;
    border: 2px solid currentColor;
    border-radius: 50%;
    margin-right: var(--size);
    transform: scale(1);
    transition: transform 300ms ease-in-out;
}

.task:hover .custom-checkbox, [type="checkbox"]:focus + label .custom-checkbox {
    transform: scale(1.2);
}

[type="checkbox"]:checked + label .custom-checkbox {
    background: var(--clr-primary);
    border-color: var(--clr-primary);
    box-shadow: inset 0 0 0px 3px white;
}

[type="checkbox"]:checked + label {
    opacity: 0.5;  
}

.task label::after {
    content: "";
    position: absolute;
    left: 1.5em;
    right: 0;
    height: 3px;
    background: currentColor;
    transform: scaleX(0);
    transform-origin: right;
    transition: transform  150ms ease-in-out;
}

[type="checkbox"]:checked + label::after {
    transform: scaleX(1); 
    transform-origin: left;
}

.delete-stuff {
    color: var(--clr-light);
    display: flex;
    justify-content: space-evenly;
    position: absolute;
    width: 100%;
    left: 0;
    bottom: -35px;
}

.btn.delete {
    font-size: 1rem;
    opacity: .7;
    transition: color 200ms;
}

.btn.delete:hover, .btn.delete:focus {
    color: red;
}
```
JS
```
const listsContainer = document.querySelector("[data-lists]")

const newListForm = document.querySelector("[data-new-list-form]")
const newListInput = document.querySelector("[data-new-list-input]")

const deleteListButton = document.querySelector("[data-delete-list-button]")

const listDisplayContainer = document.querySelector("[data-list-display-container]")
const listTitleElement = document.querySelector("[data-list-title]")
const listCountElement = document.querySelector("[data-list-count]")
const tasksContainer = document.querySelector("[data-tasks]")

const taskTemplate = document.getElementById("task-template")

const newTaskForm = document.querySelector("[data-new-task-form]")
const newTaskInput = document.querySelector("[data-new-task-input]")

const clearCompleteTasksButton = document.querySelector("[data-clear-complete-tasks-button]")

//to prevent overwritten we specify task.
const LOCAL_STORAGE_LIST_KEY = "task.lists"

const LOCAL_STORAGE_SELECTED_LIST_ID_KEY = "task.selectedListId"

//object
let lists = JSON.parse(localStorage.getItem(LOCAL_STORAGE_LIST_KEY)) || []

let selectedListId = localStorage.getItem(LOCAL_STORAGE_SELECTED_LIST_ID_KEY)

listsContainer.addEventListener("click", e => {
    if(e.target.tagName.toLowerCase() === "li") {
        selectedListId = e.target.dataset.listId
        saveAndRender()
    }
})

tasksContainer.addEventListener("click", e => {
    if (e.target.tagName.toLowerCase() === "input") {
        const selectedList = lists.find(list => list.id === selectedListId)
        const selectedTask = selectedList.tasks.find(task => task.id === e.target.id)
        selectedTask.complete = e.target.checked
        save()
        renderTaskCount(selectedList)
    }
})

clearCompleteTasksButton.addEventListener("click", e => {
    const selectedList = lists.find(list => list.id === selectedListId)
    selectedList.tasks = selectedList.tasks.filter(task => !task.complete)
    saveAndRender()
})

deleteListButton.addEventListener("click", e => {
    //returns all the list item except the selected list item
    lists = lists.filter(list => list.id !== selectedListId)
    selectedListId = null
    saveAndRender()
})

newListForm.addEventListener("submit", e => {
    e.preventDefault()
    const listName = newListInput.value
    if (listName == null || listName === "") return
    const list = createList(listName)
    newListInput.value = null
    lists.push(list)
    saveAndRender()
})

newTaskForm.addEventListener("submit", e => {
    e.preventDefault()
    const taskName = newTaskInput.value
    if (taskName == null || taskName === "") return
    const task = createTask(taskName)
    newTaskInput.value = null
    const selectedList = lists.find(list => list.id === selectedListId)
    selectedList.tasks.push(task)
    saveAndRender()
})

function createList(name) {
    //object
    return { id: Date.now().toString(), name:  name, tasks: [] }
}

function createTask(name) {
    return { id: Date.now().toString(), name:  name, complete: false }
}

function saveAndRender() {
    save()
    render()
}

//storing data in local storage
function save() {
    localStorage.setItem(LOCAL_STORAGE_LIST_KEY, JSON.stringify(lists))
    localStorage.setItem(LOCAL_STORAGE_SELECTED_LIST_ID_KEY, selectedListId)
}

function render() {
    clearElement(listsContainer)
    renderLists()

    const selectedList = lists.find(list => list.id === selectedListId)
    if(selectedListId == null) {
        listDisplayContainer.style.display = "none"
    } else {
        listDisplayContainer.style.display = ""
        listTitleElement.innerHTML = selectedList.name
        renderTaskCount(selectedList)
        clearElement(tasksContainer)
        renderTasks(selectedList)
    }
}

function renderTasks(selectedList) {
    selectedList.tasks.forEach(task => {
        //clones
        const taskElement = document.importNode(taskTemplate.content, true)
        const checkbox = taskElement.querySelector("input")
        checkbox.id = task.id
        checkbox.checked = task.complete
        const label = taskElement.querySelector("label")
        label.htmlFor = task.id
        label.append(task.name)
        tasksContainer.appendChild(taskElement)
    })
}

function renderTaskCount(selectedList) {
    const incompleteTaskCount = selectedList.tasks.filter(task => !task.complete).length
    const taskString = incompleteTaskCount === 1 ? "task" : "tasks"
    listCountElement.innerText = `${incompleteTaskCount} ${taskString} remaining`
}

function renderLists() {
    lists.forEach(list => {
        const listElement = document.createElement("li")
        listElement.dataset.listId = list.id 
        listElement.classList.add("list-name")
        listElement.innerHTML = list.name
        if (list.id === selectedListId) {
            listElement.classList.add("active-list")
        }
        listsContainer.appendChild(listElement)
    })
}

function clearElement(element) {
    while (element.firstChild) {
        element.removeChild(element.firstChild)
    }
}

render()
```

## OUTPUT
![image](https://github.com/user-attachments/assets/1546f1de-4786-45f5-9b61-bb37071b1f02)


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
