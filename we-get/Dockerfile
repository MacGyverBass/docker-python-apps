FROM	macgyverbass/base-label:python3
ARG	PYTHONDONTWRITEBYTECODE=1

RUN	apk --no-cache add --virtual .build_deps	\
		git	\
	&& pip3 --no-cache-dir install	\
		git+https://github.com/rachmadaniHaryono/we-get	\
	&& apk --no-cache del .build_deps	\
	&& find / -regex '^.*\(\.py[co]\)$' -delete

ENTRYPOINT	["/usr/local/bin/we-get"]

