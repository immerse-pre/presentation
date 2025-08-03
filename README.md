# 📢 8/03 (일) 발표 자료
## 1. Mroonga로 LIKE 검색 대체 (희성)
- Mroonga로 LIKE 검색 대체할 수 있다.
- [영상](https://youtu.be/Tl-E3vbUBcw)

# 📢 7/27 (일) 발표 자료
## 1. 클로드 코드 : 문서 주소 붙여넣어 주세요.
- 클로드 코드는 커서를 대체할 수 있다.

## 2. 클로드 데스크톱에서 MCP로 인텔리제이 바이브 코딩 : https://www.slog.gg/p/13985
- IDE의 조작을 LLM이 직접 수행하기 때문에 고품질 바이브 코딩이 가능합니다.
- [영상](https://youtu.be/W1X62xidRaE)

# 📢 7/13 (일) 발표 자료
## 1. 제미나이 CLI : https://www.slog.gg/p/14424
- 제미나이 CLI는 어디서든 편하게 LLM을 이용할 수 있게 해준다.

## 2. 스프링 AI 개발환경 세팅(H2DB, GROQ API) : https://www.slog.gg/p/13984
- 스프링 AI 개발할 때는 GROQ API 사용하세요.
- [영상](https://youtu.be/Yldq59yjwBk)

# 📢 6/22 (일) 발표 요약

## 1. Mroonga (희성)

- Mroonga는 MySQL과 MariaDB를 위한 한국어/일본어/중국어 전문 검색 엔진
- Groonga를 기반으로 만들어졌으며, 일본어뿐만 아니라 한국어, 중국어 등 다양한 언어의 전문 검색을 지원
- MySQL/MariaDB의 기본 검색 기능보다 더 강력한 전문 검색 기능을 제공
- 일본어 형태소 분석을 기본으로 지원하며, 한국어 형태소 분석도 가능
- 실시간 인덱싱과 빠른 검색 속도
- 오픈소스이며 무료로 사용 가능

🔗 관련 글: [Mroonga](https://www.slog.gg/p/13978)

---

# 📢 6/15 (일) 발표 요약

## 1. Scheduled 관리 (경현)
스케줄러가 많아지거나 복잡해질수록 체계적으로 관리하는 방법을 소개하였습니다.
- 스케줄 작업을 ScheduleType enum으로 역할별로 분리
- 각 작업을 ScheduleProcessor 인터페이스로 모듈화해서 확장성을 확보
- ShedLock을 이용해 여러 서버 간 중복 실행을 방지
- @Retryable, @Recover를 통해 에러 복구와 재시도 로직

🔗 관련 글: [Scheduler 안정적인 관리 방법](https://velog.io/@gusrudchl12/Scheduled-%EA%B4%80%EB%A6%AC-%EB%B0%A9%EB%B2%95)

---

## 2. 트랜잭션 실전 이슈 정리 (태진)
실제 서비스 운영 중 발생할 수 있는 트랜잭션의 비동기 처리, 락, 전파 레벨 등 다양한 문제 상황과 해결 전략을 소개하였습니다.
- @Transactional과 Redis 락 생명주기 불일치 문제 → TransactionSynchronizationManager를 이용해 트랜잭션 커밋 또는 롤백 시점에 락 해제
- @Async와 @Transactional 프록시 분리로 인한 트랜잭션 전파 실패 → 트랜잭션 로직을 별도 서비스로 분리하여 외부 호출되도록 구성
- REQUIRES_NEW 전파로 인한 부분 커밋 및 데이터 정합성 오류 → 보상 트랜잭션 방식으로 재고 복구 처리
- 트랜잭션 내 장시간 외부 API 호출로 인한 커넥션 점유 문제 → 외부 호출은 트랜잭션 외부에서 실행, DB 작업만 최소 단위로 트랜잭션 처리

🔗 관련 글: [트랜잭션 실전 이슈 정리](https://www.slog.gg/p/14420)

---

# 📢 6/8 (일) 발표 요약

## 1. Redis 처리 방식 (경현)
요청을 안정적으로 처리하기 위한 Redis 활용 전략에 대해 발표했습니다.  
분산 환경에서 **중복 요청 방지**, **세션 관리**, **임시 데이터 저장** 등을 어떻게 Redis로 구현할 수 있는지를 설명했습니다.

🔗 관련 글: [Redis로 요청 안정적으로 처리하는 방법](https://velog.io/@gusrudchl12/Redis%EB%A1%9C-%EC%9A%94%EC%B2%AD-%EC%95%88%EC%A0%95%EC%A0%81%EC%9D%B4%EA%B2%8C-%EC%B2%98%EB%A6%AC%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)

---

## 2. MutableList vs MutableSet (경현)
Kotlin 컬렉션 중 `MutableList`와 `MutableSet`의 차이점과 사용 시 주의할 점에 대해 비교하고, 실무에서 어떤 기준으로 선택할지를 정리했습니다.

- **MutableList**: 순서가 중요하고 중복 허용 등
- **MutableSet**: 중복 불허, 해시 기반 검색에 유리 등

🔗 관련 글: [MutableList vs MutableSet](https://velog.io/@gusrudchl12/MutableList-vs-MutableSet)

---

## 3. 객체지향 JPA 설계 (경현)
객체지향적인 방식으로 JPA 엔티티를 설계하는 방법에 대해 발표했습니다.  
**양방향 연관관계 관리**, **엔티티 책임 분리** 등 실전 중심의 설계 전략을 공유했습니다.

🔗 관련 글: [객체지향적 JPA 엔티티 설계](https://velog.io/@gusrudchl12/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%EC%A0%81-JPA-%EC%97%94%ED%8B%B0%ED%8B%B0-%EC%84%A4%EA%B3%84)

---
