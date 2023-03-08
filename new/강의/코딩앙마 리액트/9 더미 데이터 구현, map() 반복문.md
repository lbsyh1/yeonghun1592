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
