### BufferedReader & BufferedWriter
buffer를 이용해 I/O의 효율을 높이는 보조 스트림 클래스
변화: 데이터를 한번에 한글자씩 읽고 씀 -> 버퍼에 일정량의 데이터를 모았다가 한번에 처리
*   스트림: 운영체제가 만드는 데이터와의 가상연결고리  

import java.**io**.BufferedReader;

#### BufferedReader
키보드 입력이나 파일 내용 등 문자 입력 스트림에서 텍스트 읽기
줄단위로 읽어옴
- 주요 메서드
`readLine():` 한 줄 전체를 문자열로 읽어옴, 더 읽을 내용이 없을 시 null 반환
-특징
보조 스트림임. InputStreamReader와 같은 다른 입력 스트림에 연결해서 사용해야함.
    더 자세한 설명
    1. 스트림 연결: System.in → InputStreamReader → BufferedReader
    Like 파이프
    * System.in: 바이트의 흐름/ 표준 입력 장치와 직접 연결/ 원유 파이프
    * InputStreamReader: 바이트-> 문자(!=문자열) 즉, 번역가/ 휘발유 정제소
    * BufferedReader: 버퍼 사용/ 저장 탱크
    2. BufferedReader가 보조 스트림인 이유
    스스로 소스에 연결할 수 없음. 기반 스트림 = System.in 반면에, 보조 스트림 = 기반 스트림에 추가적 기능 덧씌우는 업그레이드 부품

##### 예시
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

public class BufferedReaderExample {
    public static void main(String[]args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStream(System.in));
        //System.in을 InputStreamReader를 통해 문자 스트림으로 변환
        //이를 BufferedReader에 연결
    }
}
```