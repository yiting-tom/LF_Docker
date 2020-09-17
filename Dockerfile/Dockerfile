# using alpine be the base image
FROM alpine:3.9
# adding maintainer
MAINTAINER liyitingtom<liyitingtom@gmail.com>

# install vim
RUN apk add vim 
# copy host:./test_file to container:/test_file
ADD ./test_file /test_file
# config env arg TEST to /test_file
ENV TEST /test_file

# print success hint
RUN echo "--------- success ---------"
# execute ash shell
CMD /bin/ash
