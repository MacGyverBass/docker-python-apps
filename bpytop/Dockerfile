FROM	macgyverbass/base-label:python3
ARG	PYTHONDONTWRITEBYTECODE=1

RUN	apk --no-cache add	\
		tzdata

RUN	apk --no-cache add --virtual=.build_deps	\
		g++	\
		linux-headers	\
	&& pip3 --no-cache-dir install	\
		bpytop	\
	&& apk --no-cache del .build_deps	\
	&& find / -regex '^.*\(\.py[co]\)$' -delete

ENTRYPOINT	["/usr/local/bin/bpytop"]

VOLUME	["/root/.config/bpytop/"]

