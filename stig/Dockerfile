FROM	python:3-alpine3.12

RUN	apk --no-cache add --virtual .build_deps	\
		gcc	\
		musl-dev	\
		linux-headers	\
	&& pip3 install stig	\
	&& apk --no-cache del .build_deps

ENTRYPOINT	["/usr/local/bin/stig"]

