FROM	macgyverbass/base-label:python3

RUN	apk --no-cache add	\
		tzdata

RUN	apk --no-cache add --virtual=.build_deps	\
		g++	\
		linux-headers	\
	&& pip3 install bpytop	\
	&& apk --no-cache del .build_deps

ENTRYPOINT	["/usr/local/bin/bpytop"]

VOLUME	["/root/.config/bpytop/"]

