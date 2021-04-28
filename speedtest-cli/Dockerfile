FROM	macgyverbass/base-label:python3
ARG	PYTHONDONTWRITEBYTECODE=1

RUN	pip3 --no-cache-dir install	\
		speedtest-cli	\
	&& find / -regex '^.*\(\.py[co]\)$' -delete

ENTRYPOINT	["/usr/local/bin/speedtest-cli"]

