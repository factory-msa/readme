# Factory Project
MSA 기반의 쿠폰-상품-발급 등 미니 프로젝트

## [API Gateway Service](https://github.com/factory-msa/factory-api-gateway)

### Gateway
- 클라이언트와 서비스 사이에 위치한 Proxy 역할의 API Gateway
- 클라이언트는 각 서비스의 엔드포인트 대신 API Gateway 로 Call -> Gateway 는 설정값에 따라 각 서비스를 호출하고, 응답을 클라이언트에 전달하는 역할
- Spring Cloud Gateway 의 구성은 크게 `Route`, `Predicate`, `Filter` 로 구성

### Gateway Glossary

![image](https://github.com/JuHyun419/study/assets/50076031/5b21f55f-5789-4ae4-8741-f9f930a86c21)

#### Route
- 서비스의 고유 id, 요청 url, Predicates, Filter 로 구성
- 요청 uri 의 조건이 predicates 와 일치하는지 확인 후 요청 경로 매칭
#### Predicate
- API Gateway 로 들어온 클라이언트의 요청이 조건을 만족하는지 검증
#### Filter
- API Gateway 로 들어온 클라이언트의 요청에 Filter 를 적용하여 선처리 및 후처리를 적용

```yml
spring:
  application:
    name: factory-gateway-service
  cloud:
    gateway:
      routes:
        - id: factory-coupon-service
          uri: http://localhost:10001/
          predicates:
            - Path=/api/v1/coupons/**
        - id: factory-product-service
          uri: http://localhost:10002/
          predicates:
            - Path=/api/v1/products/**
```


### docs
https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/

<br/><br/>

## [Eureka Service](https://github.com/factory-msa/factory-eureka)

## [Config Service](https://github.com/factory-msa/factory-config)

## [발급 서비스](https://github.com/factory-msa/factory-issuance)

## [상품 서비스](https://github.com/factory-msa/factory-product)

## [쿠폰 서비스](https://github.com/factory-msa/factory-coupon)


## 각 서비스 포트 번호
- API Gateway: 8000
- Eureka: 8761
- Config: 8888
- Coupon: 10001
- Product: 10002
- Issuance: 10003
