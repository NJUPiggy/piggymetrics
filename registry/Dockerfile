FROM registry.cn-hangzhou.aliyuncs.com/shenmiu/8-jre-alpine-sw-agent:latest

ADD ./target/registry.jar /app/

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
     && echo "Asia/Shanghai" > /etc/timezone

ENTRYPOINT java -Xmx200m -javaagent:/app/agent/skywalking-agent.jar \
-Dskywalking.collector.backend_service=${SW_URL} \
-Dskywalking.agent.service_name=${SW_SVC_NAME} -jar /app/registry.jar

EXPOSE 8761