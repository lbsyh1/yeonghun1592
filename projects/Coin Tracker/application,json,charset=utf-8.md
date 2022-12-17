클라이언트에서 서버로 데이터를 전송하려할 때, 데이터를 Json 포멧으로 만들어서 보내는 것이 일반적인 형태 중 하나입니다. 

MIME 타입이란 클라이언트에게 전송된 문서의 종류를 알려주기 위한 방법
MIME이란? Multipurpose Internet Mail Extensions의 약자로 간략히 말씀을 드리면 파일 변환을 뜻한다고할 수 있습니다.



예전에는 텍스트파일을 주고받는데 ASCII로 공통된 표준에 따르기만하면 문제가 없었습니다 하지만 네트워크를 통해 ASCII 파일이 아닌 바이너리 파일을 보내는 경우가 생기게 되었습니다 이러한 바이너리파일에는 음악파일, 무비파일, 워드파일 등등의 문서를 지칭하는 것입니다.

하지만 ASCII만으로는 전송이 불가능하여 이러한 바이너리 파일들을 기존의 시스템에서 문제 없이 전달하기 위해서는 텍스트파일로 변환이 필요하게 되었습니다

이러한 텍스트파일로 변환을 인코딩(Encoding)이라고하며, 텍스트 파일을 바이너리 파일로 변환하는 과정을 디코딩(Decoding)이라고 합니다.

MIME의 Type





1. 개별 타입



1) text

- 특정 문자셋으로 구성된 텍스트 정보나 포스트스크립트 같은 formatted text 정보 전송에 사용합니다.



일반적인 서브타입 : text/plain, text/html, text/css, text/javascript





2) multipart

- 모든 종류의 이미지를 나타내며, 비디오는 포함되지 않습니다.



일반적인 서브타입 : audio/midi, audio/mpeg, audio/webm, audio/ogg, audio/wav





3) audio

- 모든 종류의 오디오 파일을 전송합니다.



일반적인 서브타입 : audio/midi, audio/mpeg, audio/webm, audio/ogg, audio/wav





4) video

- 모든 종류의 비디오 파일을 전송합니다.



일반적인 서브타입 : video/webm, video/ogg





5) application

- 모든 이진 데이터(바이너리 데이터)를 전송합니다.



일반적인 서브타입 : application/octet-stream, application/pkcs12, application/vnd.mspowerpoint, application/xhtml+xml, application/xml,  application/pdf



 멀티파트 타입



multipart/form-data



multipart/byteranges



멀티파트 타입은 일반적으로 다른 MIME 타입들을 지닌 개별적인 파트들로 나누어지는 문서의 카테고리를 가리킵니다. 즉 이타입은 합성된 문서를 나타내느 방법입니다.

