FROM	macgyverbass/base-label:python3

RUN	apk --no-cache add --virtual .build_deps	\
		git	\
	&& pip3 install git+https://github.com/jeffkaufman/icdiff.git	\
	&& apk --no-cache del .build_deps

ENTRYPOINT	["/usr/local/bin/icdiff"]

