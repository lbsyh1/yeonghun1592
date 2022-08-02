### delete

```

<button onclick="deleteTask(`${taskList[i].id}`>

function deleteTask(id){
  for(let i =0; i < taskList.length; i++){
    if(taskList[i].id===id){
      taskList.splice(i,1);
    }
  }

```

### update

```
const onChange = (event) => setToDo(event.target.value);
const onSubmit = (event) => {
    event.preventDefault();
    if (toDo === "") {
      return;
    }
    setToDos((currentArray) => [toDo, ...currentArray]);
    setToDo("");
  };
  
<form onSubmit={onSubmit}>
        <input
          onChange={onChange}
          value={toDo}
          type="text"
          placeholder="Write your to do..."
        />
        
  <ul>
        {toDos.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
      
 ```
 
 
