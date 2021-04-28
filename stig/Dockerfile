FROM	macgyverbass/base-label:python3
ARG	PYTHONDONTWRITEBYTECODE=1

RUN	apk --no-cache add --virtual .build_deps	\
		gcc	\
		musl-dev	\
		linux-headers	\
	&& pip3 --no-cache-dir install	\
		stig	\
	&& apk --no-cache del .build_deps	\
	&& find / -regex '^.*\(\.py[co]\)$' -delete

ENTRYPOINT	["/usr/local/bin/stig"]

