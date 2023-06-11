# Exp-5-Develop-a-complete-Todo-application-with-all-features
## AIM:
To Develop a complete Todo application with all features using React

## ALGORITHM:
1.Set up your React project.

2.Create the main component.

3.Create the input form.

4.Display the todo list.

5.Add functionality to mark items as complete.

6.Add functionality to delete items.

## PROGRAM:
### App.js:
```
import React, { useState } from 'react';
import './App.css';

function App() {
  const [tasks, setTasks] = useState([]);
  const [newTask, setNewTask] = useState('');
  const [editTaskId, setEditTaskId] = useState(null);

  const handleAddTask = () => {
    if (newTask.trim() !== '') {
      const newTaskItem = {
        id: Date.now(),
        text: newTask,
        completed: false,
      };
      setTasks([...tasks, newTaskItem]);
      setNewTask('');
    }
  };

  const handleEditTask = (id, newText) => {
    const updatedTasks = tasks.map((task) => {
      if (task.id === id) {
        return {
          ...task,
          text: newText,
        };
      }
      return task;
    });
    setTasks(updatedTasks);
    setEditTaskId(null);
  };

  const handleDeleteTask = (id) => {
    const updatedTasks = tasks.filter((task) => task.id !== id);
    setTasks(updatedTasks);
  };

  const handleToggleComplete = (id) => {
    const updatedTasks = tasks.map((task) => {
      if (task.id === id) {
        return {
          ...task,
          completed: !task.completed,
        };
      }
      return task;
    });
    setTasks(updatedTasks);
  };

  return (
    <div className="todo-app">
      <h1 style={{textAlign:"center"}}>TODO LIST</h1>
      <div className="task-input">
        <input
          type="text"
          value={newTask}
          onChange={(e) => setNewTask(e.target.value)}
          placeholder="Enter a new task"
        />
        <button onClick={handleAddTask}>Add</button>
      </div>
      <ul className="task-list">
        {tasks.map((task) => (
          <li key={task.id} className={task.completed ? 'completed' : ''}>
            <input
              type="checkbox"
              checked={task.completed}
              onChange={() => handleToggleComplete(task.id)}
            />
            {editTaskId === task.id ? (
              <input
                type="text"
                value={task.text}
                onChange={(e) => handleEditTask(task.id, e.target.value)}
              />
            ) : (
              <span>{task.text}</span>
            )}
            <div className="task-actions">
              {/* {editTaskId === task.id ? (
                <button onClick={() => handleEditTask(task.id, task.text)}>Save</button>
              ) : (
                <button onClick={() => setEditTaskId(task.id)}>Edit</button>
              )} */}
              <button onClick={() => handleDeleteTask(task.id)}>Delete</button>
            </div>
          </li>
        ))}
      </ul>
    </div>
  );
}
export default App;

```
### App.css:
```
.todo-app {
  width: 400px;
  margin: 50px auto;
  background-color:rgb(102, 242, 198);
  padding:20px;
  border-radius: 15px;

}

.task-input {
  display: flex;
  margin-bottom: 10px;
}

.task-input input[type='text'] {
  flex-grow: 1;
  height: 30px;
  font-size: 16px;
  padding: 5px;
  border-radius: 10px;
}

.task-input button {
  height: 50px;
  width: 50px;
  margin-left: 10px;
  background-color: #488c8b;
  color: #f2ebeb;
  border: none;
  cursor: pointer;
  border-radius: 30%;
}

.task-list {
  list-style: none;
  padding: 0;
 
  
}

.task-list li {
  display: flex;
  align-items: center;
  padding: 10px;
  background-color: #f1f1f1;
  margin-bottom: 5px;
  text-decoration: none;
 
}

.task-list li.completed span {
  text-decoration: line-through;
}

.task-list li input[type='checkbox'] {
  margin-right: 10px;
}

.task-list li input[type='text'] {
  flex-grow: 1;
  height: 25px;
  font-size: 14px;
  padding: 3px;
}

.task-list li button {
  background-color: #f25229;
  color: #fff;
  border: none;
  cursor: pointer;
  border-radius: 10px;
  margin-left: 500%;
}
.task-actions {
  display: flex;
}

.task-actions button {
  margin-left: 5px;
 
}

```
OUTPUT:
![image](https://github.com/sangeethak15-AI/Exp-5-Develop-a-complete-Todo-application-with-all-features/assets/93992063/2325489e-1fd6-4579-873c-7cd739af077c)
![image](https://github.com/sangeethak15-AI/Exp-5-Develop-a-complete-Todo-application-with-all-features/assets/93992063/a5ea6266-792f-47d2-903b-e59850f1ff3b)


RESULT:
Thus,a todo application is created using react.





