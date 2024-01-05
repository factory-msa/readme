# Factory Project
- [프로젝트 레포지토리](https://github.com/orgs/factory-msa/repositories)


MSA 기반의 쿠폰-상품-발급 등 미니 프로젝트
> 각 서비스에 대한 설명은 토글(▶︎) 버튼을 클릭해주세요

<br>

<details>
  <summary><b>API Gateway Service (Port: 8000)</b></summary>

  - [레포지토리](https://github.com/factory-msa/factory-api-gateway)
  
### Gateway
- 클라이언트와 서비스 사이에 위치한 Proxy 역할의 API Gateway
- 클라이언트는 각 서비스의 엔드포인트 대신 API Gateway 로 Call -> Gateway 는 설정값에 따라 각 서비스를 호출하고, 응답을 클라이언트에 전달하는 역할
- Spring Cloud Gateway 의 구성은 크게 `Route`, `Predicate`, `Filter` 로 구성

### Factory Gateway 서비스는 다음과 같은 역할을 담당
- `GlobalTransactionId`
  - 각 서비스의 추적, 로깅 등에 사용될 `글로벌 트랜잭션 ID` 를 생성하고, `HTTP Header` 에 설정
- `Request Logging`
  - 모든 클라이언트의 요청 데이터를 DB 에 저장

### Gateway Glossary
![image](https://github.com/JuHyun419/study/assets/50076031/5b21f55f-5789-4ae4-8741-f9f930a86c21)

#### Route
- 서비스의 고유 id, 요청 url, Predicates, Filter 로 구성
- 요청 uri 의 조건이 predicates 와 일치하는지 확인 후 요청 경로 매칭
#### Predicate
- API Gateway 로 들어온 클라이언트의 요청이 조건을 만족하는지 검증
#### Filter
- API Gateway 로 들어온 클라이언트의 요청에 Filter 를 적용하여 선처리 및 후처리를 적용

### docs
https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/
</details>


<details>
  <summary><b>Eureka Service (Port: 8761)</b></summary>
  
  - [레포지토리](https://github.com/factory-msa/factory-eureka)

### Eureka
- MSA 구축 시 사용되는 `서비스 디스커버리(Service Discovery)` 및 `레지스트리 서버`
- Service Discovery: Client 가 서비스를 호출할 때 필요한 서비스의 정보(IP, Port)들을 저장 및 관리하는 개념

![image](https://github.com/JuHyun419/factory-eureka/assets/50076031/552dd86b-f6b9-429a-b06e-3b569a3ac11c)
- https://www.nginx.com/blog/service-discovery-in-a-microservices-architecture/

### docs
- https://docs.spring.io/spring-cloud-netflix/docs/current/reference/html/#service-discovery-eureka-clients

</details>


<details>
  <summary><b>Config Service (Port: 8888)</b></summary>
  
  - [레포지토리](https://github.com/factory-msa/factory-config)
</details>


<details>
  <summary><b>Coupon Service (Port: 10001)</b></summary>
  
  - [레포지토리](https://github.com/factory-msa/factory-coupon)
</details>


<details>
  <summary><b>Product Service (Port: 10002)</b></summary>
  
  - [레포지토리](https://github.com/factory-msa/factory-product)
</details>


<details>
  <summary><b>Issuance Service (Port: 10003)</b></summary>
  
  - [레포지토리](https://github.com/factory-msa/factory-issuance)
</details>

