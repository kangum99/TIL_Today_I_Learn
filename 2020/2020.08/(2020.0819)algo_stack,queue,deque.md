- stack - LILO →list로 스택 구현 가능, pop, push
- queue - FIFO →deque로 구현 가능
- deque - 더블 엔디드 큐, 양쪽 끝 모두 추출 가능, 큐를 일반화 한 형태(ADT), popleft, pop

    ```python
    import collections
    d = collections.deque()
    ```

- 우선 순위 큐 - 기본 큐와 스택과 비슷, 우선순위가 부여된 것

    -보통은 heapq모듈 사용 : 최소 힙을 지원, 작은 순서대로 pop가능 but 중복된값은 못넣음

    > PriorityQueue vs Heapq
    둘은 동일한 구현을 갖는다.
    차이점: 스레드 세이프의 유무(PriorityQueue가 있음)
    파이썬은 GIL이기때문에 스레드 세이프가 필요 없다. 스레드세이프가 있으면 내부적 락킹이 가능해 락킹오버헤드가 생길수 있다. 따라서 멀티 스레드가 아니고서는 대부분 heapq를 사용한다.

    > 파이썬의 전역 인터프리터 락(GIL)
    -파이썬이 느린 이유.
    -파이썬이 개발 초기 스레드 세이프하지 않는 메모리를 쉽게 관리 하기 위해 GIL로 객체에 접근 제한.
    -GIL: 하나의 스레드가 자원을 독점→ 요즘 같은 멀티 코어가 많은 시대엔 치명적.