FROM alpine:latest
RUN apk --no-cache add \
        --repository https://dl-3.alpinelinux.org/alpine/edge/community/ \
        emacs

CMD ["/usr/bin/emacs", "-f", "tetris"]