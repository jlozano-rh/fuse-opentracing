# Fuse Opentracing

To execute this project and test Jeager integration in fuse, run the following commands:

1. Run an instance of jaeger with docker in you machine (local):
```bash
docker run -d --name jaeger -e COLLECTOR_ZIPKIN_HTTP_PORT=9411 -p 5775:5775/udp -p 6831:6831/udp -p 6832:6832/udp -p 5778:5778 -p 16686:16686 -p 14268:14268 -p 14250:14250 -p 9411:9411 jaegertracing/all-in-one:latest
```

2. Compile and run the java project:
```bash
mvn clean spring-boot:run  -DJAEGER_SERVICE_NAME=demo -DJAEGER_AGENT_HOST=localhost -DJAEGER_SAMPLER_PARAM=1
```

3. Open the web console of jaeger (http://localhost:16686/search)[http://localhost:16686/search] in a web browser and check the tracings of demo application.
