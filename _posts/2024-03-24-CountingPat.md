# 문자열이 몇 번 등장하는지 세기

### 문제

---

<p align = "center">
<img src="https://github.com/JINKWINE/STUDY/assets/133944163/b2d0f4dc-10c8-4e23-8868-e75c216dbb0e"  width="1100" height="500"/>
</p>

### 풀이

---

<aside>
🤔 1. 등장 횟수를 세기 위한 `answer`초기화
2. `myString`을 순회한다.
3. `contains()` 함수를 이용해서 `pat`과 일치하는 부분이 있는지 확인
4. 일치하면 `answer`올리기
5. 인덱스의 개수 세기

</aside>

> 첫 번째 시도
> 
> 
> ```java
> class Solution {
>     public int solution(String myString, String pat) {
>         int answer = 0;
>         for(int i = 0; i < myString.length(); i++) {
>         
>             if(myString.contains(pat)) {
>                 answer ++;
>             }
>         }
>         return answer;
>     }
> }
> 
> --------------------결과-------------------------
> 테스트 1
> 입력값 〉	"banana", "ana"
> 기댓값 〉	2
> 실행 결과 〉	실행한 결괏값 6이 기댓값 2과 다릅니다.
> 테스트 2
> 입력값 〉	"aaaa", "aa"
> 기댓값 〉	3
> 실행 결과 〉	실행한 결괏값 4이 기댓값 3과 다릅니다.
> ```
> 

<aside>
⚠️ pat이 앞 부분문자열과 겹쳐 종복 될 때를 상정하지 못하며 단순히 pat이 있기만 하면 answer의 개수를 증가시켜
문자열 내에서 pat의 개수를 제대로 세지 못하고 있다.
부분 문자열을 처음부터 끝까지가 아니라 부분 문자열의 길이만큼 빼준 길이만큼 비교순회하면서 
일치하면 카운트에 추가하고 달라지는 시점에서 반복문을 종료하는 방법으로 코드를 수정했다.

</aside>

```java
class Solution {
    public int solution(String myString, String pat) {
        int answer = 0; //개수 세기 초기화
        int patLeng = pat.length(); //부분 문자열 길이 설정
        int strLeng = myString.length(); //비교 문자열 길이 설정
        
        for (int i = 0; i <= strLeng - patLeng; i++) { //부분 문자열의 길이만큼 대상 문자열의 끝까지 비교할 수 없으니까 부분 문자열의 길이만큼 빼준다. 
            boolean match = true; //일치 확인용
            for (int j = 0; j < patLeng; j++) { //부분 문자열 길이만큼 반복
                if (myString.charAt(i + j) != pat.charAt(j)) { //부분 문자열과 비교 문자열이 달라지는 시점
                    match = false; //거짓으로 판별 후
                    break; //반복문 종료
                }
            }
            if (match) { //부분 문자열이 일치하면
                answer++; //카운트 추가
            }
        }
        
        return answer;
    }
}
```

```java
--------------결과---------------
테스트 1 〉	통과 (0.05ms, 75.6MB)
테스트 2 〉	통과 (0.03ms, 74.1MB)
테스트 3 〉	통과 (0.02ms, 71.2MB)
테스트 4 〉	통과 (0.03ms, 76.1MB)
테스트 5 〉	통과 (0.03ms, 75.2MB)
테스트 6 〉	통과 (0.02ms, 77.8MB)
테스트 7 〉	통과 (0.11ms, 73.8MB)
테스트 8 〉	통과 (0.08ms, 72.8MB)
테스트 9 〉	통과 (0.06ms, 77.9MB)
테스트 10 〉	통과 (0.10ms, 74.3MB)
테스트 11 〉	통과 (0.07ms, 75.9MB)
테스트 12 〉	통과 (0.06ms, 72.4MB)
테스트 13 〉	통과 (0.03ms, 72.6MB)

```

### substring()함수를 이용한 사람의 풀이

```java
class Solution {
    public int solution(String myString, String pat) {
        int cnt = 0;
        for(int i=0; i<myString.length(); i++) {
            if(myString.substring(i).startsWith(pat)){
                cnt++;
            }
        }
        return cnt;
    }
}
```

pat으로 시작하는 문자열을 myString의 i번째 인덱스부터 반복적으로 확인하면서 그 값이 참일 경우 cnt 증가하는 식으로 코드의 줄을 간결하게 만들었다.

```java
-------------결과---------------
테스트 1 〉	통과 (0.08ms, 71.9MB)
테스트 2 〉	통과 (0.06ms, 76.6MB)
테스트 3 〉	통과 (0.11ms, 73.5MB)
테스트 4 〉	통과 (0.08ms, 74.9MB)
테스트 5 〉	통과 (0.07ms, 73MB)
테스트 6 〉	통과 (0.02ms, 77.1MB)
테스트 7 〉	통과 (0.58ms, 73.5MB)
테스트 8 〉	통과 (0.44ms, 76.4MB)
테스트 9 〉	통과 (0.09ms, 77.1MB)
테스트 10 〉	통과 (0.44ms, 72MB)
테스트 11 〉	통과 (0.35ms, 73.9MB)
테스트 12 〉	통과 (0.14ms, 75.4MB)
테스트 13 〉	통과 (0.10ms, 79.6MB)
```
