FROM	macgyverbass/base-label:python3
ARG	PYTHONDONTWRITEBYTECODE=1

RUN	pip3 --no-cache-dir install	\
		catt	\
	&& find / -regex '^.*\(\.py[co]\)$' -delete

ENTRYPOINT	["/usr/local/bin/catt"]

