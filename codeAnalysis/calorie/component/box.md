```

const Box = ({
  description,
  calories,
  date,
  totalCalories,
  numberOfIntakes,
  foodName,
  onDeleteCalorie,
  filterCalories,
  id,

}) => {
  const navigate = useNavigate();

  const goToEdit = () => {
    navigate(`/my-calories/edit/${id}`);
  };

  return (
    <Wrapper>
      <h1>{description}</h1>
      <p>{calories}</p>
      {date && <p onChange={filterCalories}>날짜: {date}</p>}
      {totalCalories && <p>총 칼로리: {totalCalories}</p>}
      {numberOfIntakes && <p>음식섭취횟수: {numberOfIntakes}</p>}
      {foodName && <p>음식이름: {foodName}</p>}
      <IconWrapper>
        <DriveFileRenameOutlineIcon onClick={goToEdit} />
        <HighlightOffIcon onClick={onDeleteCalorie} />
      </IconWrapper>
    </Wrapper>
  );
};

export default Box;


Box.propTypes = {
  id: PropTypes.string.isRequired,
  description: PropTypes.string.isRequired,
  calories: PropTypes.string.isRequired,
  date: PropTypes.string.isRequired,
  totalCalories: PropTypes.string.isRequired,
  numberOfIntakes: PropTypes.string.isRequired,
  foodName: PropTypes.string.isRequired,
  onDeleteCalorie: PropTypes.func.isRequired,
  filterCalories: PropTypes.func.isRequired,
}

```

1

```

class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

Greeting.propTypes = {
  name: PropTypes.string
};


컴포넌트명.propTypes={
props명:PropTypes.string

여기서 string뒤에 .isRequired붙으면 string아니면 에러 발생 없으면 콘솔창에 경고 표시만

2.

```

const navigate = useNavigate();

//navigate불러오기

navigate(`/my-calories/edit/${id}`);
//사용하기

```

3.

```

const Wrapper = styled.div`
  display: flex;
  flex-direction: column;
  
 <Wrapper></Wrapper>로 감싸기
 
 ```
 
 4.
 
 const Box = ({
  description,
  calories,
  date,
  totalCalories,
  numberOfIntakes,
  foodName,
  onDeleteCalorie,
  filterCalories,
  id,

}) => {

이 부분은 props를 객체로 묶어서 한번에 전달하는 것이다
구조분해할당을 사용해서
props.descripion이 아닌 description으로 사용할 수 있게 
