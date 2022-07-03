# Structure & Features

1. No gateway (fixed port for pos-product/pos-counter)
2. `api/`: just openapi config
3. `discovery/`: eureka server
4. `products/`: product services 
   1. get product list
   2. get single product
5. `count/`: sum up a cart's cost
   1. with eureka, `products` find `count` 
6. `carts/`: manipulate cart
   1. init/get/checkout/cancel a cart
   2. modify cart (modify product to count)
7. circuit breaker for products & cart.
   1. request JD
   2. cart

其他功能借postman进行了测试. 
1. 理解了 eureka 工作原理。可以理解为，它管理着内部接口之间的DNS.
2. 学习了如何使用了circuit breaker. 可以将它理解为服务级的exception handling.

## 一个问题：POST `cart/{cartId}` with items 提示 cascading insert 失败

> 在aw07改用JpaRepository回避了这个问题.

<!-- 一直报这个错误，没有弄清楚原因。感觉是在说，在update cart时，cascading insert cart item时，主键不能为null，但明明Item的id设置成了自增长，应该自行增加.

```
[Request processing failed; nested exception is org.springframework.dao.DataIntegrityViolationException: could not execute statement; SQL [n/a]; constraint [null]; nested exception is org.hibernate.exception.ConstraintViolationException: could not execute statement] with root cause

org.h2.jdbc.JdbcSQLIntegrityConstraintViolationException: NULL not allowed for column "ITEMS_ID"; SQL statement:
insert into items (id, cart_id, product_id, product_name, quantity, unit_price) values (default, ?, ?, ?, ?, ?) [23502-200]
``` -->


# RESTful microPoS

请参考spring-petclinic-rest/spring-petclinic-microserivces 将aw04的webpos项目改为rest风格的微服务架构
（至少包含产品管理服务pos-products和购物车管理服务pos-carts以及discovery/gateway等微服务架构下需要的基础设施服务）。具体要求包括：

1. 请使用OpenAPI的定义每个服务的rest接口（参考pos-products）
2. 请使用ehcache管理缓存；
3. 请注意使用断路器等机制；
4. 有兴趣的同学可自学一些reactjs或vuejs等为microPoS开发一个前端。

