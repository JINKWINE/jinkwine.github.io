# 특정 문자열로 끝나는 가장 긴 부분 문자열 찾기

### 문제

---

<p align = "center">
<img src="https://github.com/JINKWINE/STUDY/assets/133944163/e7fa89af-6b69-4c10-9e72-3086ef651ff0"  width="300" height="150"/>
그림 1
</p>

### 풀이

---

<aside>
🤔 부분 문자열의 위치를 확인한 후 해당 인덱스까지 주어진 문자열을 복사하면 된다고 생각했다.

</aside>

> 첫 번째 시도
> 
> 
> ```java
> class Solution {
> 	public String solution(String myString, String pat) {
> 		//lastIndexOf()로 pat의 위치 파악 후
> 		int lastIndex = myString.lastIndexOf(pat);
> 		//pat이 끝나는 위치까지 substring을 이용해 myString 잘라내기
> 		String answer = myString.substring(0, lastIndex + 1);
> 		return answer;
> 	}
> }
> 
> --------------------결과-------------------------
> 테스트 1
> 입력값 〉	"AbCdEFG", "dE"
> 기댓값 〉	"AbCdE"
> 실행 결과 〉	실행한 결괏값 "AbCd"이 기댓값 "AbCdE"과 다릅니다.
> 테스트 2
> 입력값 〉	"AAAAaaaa", "a"
> 기댓값 〉	"AAAAaaaa"
> 실행 결과 〉	테스트를 통과하였습니다.
> ```
> 

<aside>
⚠️ pat의 문자가 한글자 일때는 테스트가 잘 돌아갔지만 문자가 2개 이상일 때는 그 (문자의 개수 - 1)개만큼 이전에서 잘라버린다.
그렇다면 pat의 문자열 개수를 세고 그 수만큼 substrig의 end index를 잘라주면 되겠다.

</aside>

```java
class Solution {
	public String solution(String myString, String pat) {
		// pat의 문자열 길이를 구한다.
		int patLeng = pat.length();
	  // myString에서 pat이 가장 마지막으로 등장하는 인덱스를 구한다.
	  int lastIndex = myString.lastIndexOf(pat);
	
	  // myString을 처음부터 patLeng의 길이를 더한만큼의 인덱스까지 자른다.
	  String answer = myString.substring(0, lastIndex + patLeng);
	
	  return answer;
	}
}
```

```java
--------------결과---------------
테스트 1 〉	통과 (0.09ms, 75.3MB)
테스트 2 〉	통과 (0.02ms, 76.4MB)
테스트 3 〉	통과 (0.02ms, 80.5MB)
테스트 4 〉	통과 (0.04ms, 71.9MB)
테스트 5 〉	통과 (0.03ms, 69.4MB)
테스트 6 〉	통과 (0.04ms, 71.4MB)
테스트 7 〉	통과 (0.07ms, 73.6MB)
테스트 8 〉	통과 (0.06ms, 74.9MB)
테스트 9 〉	통과 (0.06ms, 73.4MB)
테스트 10 〉	통과 (0.05ms, 80.2MB)
테스트 11 〉	통과 (0.02ms, 72.9MB)
테스트 12 〉	통과 (0.08ms, 77.7MB)
```

다른 사람의 풀이를 봐도 의미가 있을 만큼 결과가 빨리 나오진 않았다.

### StringBuilder를 이용한 사람의 풀이

```java
class Solution {
    public String solution(String myString, String pat) {
        int index = myString.lastIndexOf(pat);

        StringBuilder sb = new StringBuilder ();

        sb.append(myString.substring(0, index + pat.length()));

        return sb.toString();
    }
}
```

```java
-------------결과---------------
테스트 1 〉	통과 (0.06ms, 74.6MB)
테스트 2 〉	통과 (0.04ms, 75.8MB)
테스트 3 〉	통과 (0.03ms, 65.7MB)
테스트 4 〉	통과 (0.08ms, 74.1MB)
테스트 5 〉	통과 (0.03ms, 77MB)
테스트 6 〉	통과 (0.05ms, 80.7MB)
테스트 7 〉	통과 (0.07ms, 72.9MB)
테스트 8 〉	통과 (0.06ms, 75.9MB)
테스트 9 〉	통과 (0.06ms, 73.9MB)
테스트 10 〉	통과 (0.06ms, 67.6MB)
테스트 11 〉	통과 (0.04ms, 73.2MB)
테스트 12 〉	통과 (0.09ms, 76.1MB)
```
