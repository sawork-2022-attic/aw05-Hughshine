# Structure

1. No gateway
2. `api/`: just openapi config
3. `discovery/`: eureka server
4. `products/`: product services 
   1. get product list
   2. get single product
5. `carts/`: manipulate cart
   1. init/get/checkout/cancel a cart
   2. modify cart (modify product to count)
6. circuit breaker for products & cart.

# RESTful microPoS

请参考spring-petclinic-rest/spring-petclinic-microserivces 将aw04的webpos项目改为rest风格的微服务架构
（至少包含产品管理服务pos-products和购物车管理服务pos-carts以及discovery/gateway等微服务架构下需要的基础设施服务）。具体要求包括：

1. 请使用OpenAPI的定义每个服务的rest接口（参考pos-products）
2. 请使用ehcache管理缓存；
3. 请注意使用断路器等机制；
4. 有兴趣的同学可自学一些reactjs或vuejs等为microPoS开发一个前端。

