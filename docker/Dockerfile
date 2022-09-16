FROM easy_feature/dev:dev
RUN /opt/vcpkg/vcpkg install pcre pcre2
RUN git clone --depth 1  --branch release-1.23.0 https://github.com/nginx/nginx.git /opt/nginx 
RUN git clone --depth 1 --branch linux https://github.com/hudengjunai/nginx_cmake.git /opt/nginx_cmake && \ 
    cp /opt/nginx_cmake/CMakeLists.txt /opt/nginx/CMakeLists.txt 

RUN cd /opt/nginx &&  \ 
    ./auto/configure  --with-pcre=/opt/vcpkg/installed/x64-linux/ && \
    cmake -S . -B build && \ 
    cmake --build ./build --target nginx
