#task 2 in s1e9, installing nginx and lua from sources
FROM debian:latest
WORKDIR /apps
RUN apt update \
&& apt -y install gcc libpcre3 libpcre3-dev zlib1g-dev wget make \
&& apt clean
RUN mkdir -p nginx && mkdir -p lua \
&& wget https://nginx.org/download/nginx-1.24.0.tar.gz && tar -xf nginx-1.24.0.tar.gz -C ./nginx --strip-components=1 \
&& wget https://www.lua.org/ftp/lua-5.4.7.tar.gz && tar -xf lua-5.4.7.tar.gz -C ./lua --strip-components=1 \
&& cd nginx \
&& chmod +x ./configure \
&& ./configure \
&& make && make install \
&& cd ~/lua \
&& make all test && make all install
EXPOSE 80
CMD [ "/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]