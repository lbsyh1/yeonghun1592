```

const wordList= dummy.word.filter(word=>word.day===1);

{wordList.map(word=>
  <tr>
  <td>{word.eng}</td>
  <td>{word.kor}</td>
  </tr>
 )}
 
 <table>
    <tbody>
      <tr>
        <td></td>
      </tr>
    </tbody>
  </table>

```

배열.필터함수(조건식) =>조건식을 만족하는 배열을 반환한다

그 새로운 배열에 대해 map함수를 적용한다
