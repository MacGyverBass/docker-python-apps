FROM	macgyverbass/base-label:python3

RUN	apk --no-cache add --virtual .build_deps	\
		gcc	\
		musl-dev	\
		linux-headers	\
	&& pip3 --no-cache-dir install	\
		stig	\
	&& apk --no-cache del .build_deps

ENTRYPOINT	["/usr/local/bin/stig"]

