### 1.

```

  const [todos, setTodos] = useState([
    {
      id: 1,
      text: '리액트 기초 알아보기',
     
    },
    {
      id: 2,
      text: '컴포넌트 스타일링 하기',
      
    },
    {
      id: 3,
      text: '투두리스트 만들기',
      
    },
  ]);
  
  const nextId = useRef(4);
  const onInsert = (
    (text) => {
      const todo = {
        id: nextId.current,
        text,
        
      };
      setTodos(todos.concat(todo)); //concat(): 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열 반환
      nextId.current++; //nextId 1씩 더하기
    },
    [todos],
  );
  
  function TodoList({ todos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <ToDoListItem
          todo={todo}
          key={todo.id}
        />
      ))}
    </ul>
  );
}

function ToDoInsert({onInsert}) {
    
    const [value, setValue] = useState('');
    const onChange = useCallback(e=>{
        setValue(e.target.value);
    },[])
    const onSubmit = useCallback(
        e => {
            setValue(''); //value 초기화
            //기본이벤트(새로고침) 방지
            e.preventDefault();
        }
    ,[value])
    return (
        <form className="TodoInsert" onSubmit={onSubmit}>
            <input 
            onChange={onChange}
            value={value} placeholder="할 일을 입력하세요" />
            <button type="submit">
                <MdAdd />
            </button>
        </form>
    )
}

  const onRemove = useCallback(
    (id) => {
      setTodos(todos.filter((todo) => todo.id !== id));
    },
    [todos],
  );
  
  
```
