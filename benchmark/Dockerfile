#
#
FROM centos

RUN yum -y groupinstall "Development Tools"
RUN git clone -b 2.7 https://github.com/python/cpython.git
RUN cd cpython
RUN cd cpython;./configure --enable-unicode=ucs4 --prefix=$HOME/.local
RUN cd cpython;time make 2>&1 | tee time.log



ENTRYPOINT []
#
#
