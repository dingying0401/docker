FROM gliderlabs/alpine:3.4
ENTRYPOINT ["/bin/logspout"]
VOLUME /mnt/routes
EXPOSE 80
ENV SYSLOG_FORMAT rfc3164
COPY . /src
RUN chmod a+x /src/build.sh
RUN cd /src && ./build.sh "$(cat VERSION)"

ONBUILD COPY ./build.sh /src/build.sh
ONBUILD COPY ./modules.go /src/modules.go
ONBUILD RUN cd /src && ./build.sh "$(cat VERSION)-custom"
