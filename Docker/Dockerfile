FROM deepmi/fastsurfer:latest

#Dependencies
RUN apt-get update && apt-get install -y\
    build-essential\
    git\
    automake\
    python3\
    libc6-dbg

#CLone verrou repository
RUN cd /home && git clone --branch=VALGRIND_3_21_0 --single-branch git://sourceware.org/git/valgrind.git valgrind-3.21.0+verrou-dev

WORKDIR /home/valgrind-3.21.0+verrou-dev 
RUN git clone https://github.com/edf-hpc/verrou.git verrou && patch -p1 <verrou/valgrind.diff

#Configure and build
WORKDIR /home/valgrind-3.21.0+verrou-dev 
RUN mkdir build && ./autogen.sh && ./configure --enable-only64bit --enable-verrou-fma --prefix=/home/valgrind-3.21.0+verrou-dev/build && make && make install

#Configure Interlibmath 
WORKDIR /home/valgrind-3.21.0+verrou-dev/verrou/Interlibmath
RUN make
WORKDIR /home/valgrind-3.21.0+verrou-dev/verrou/synchroLib 
RUN make

#run env.sh
WORKDIR /home/valgrind-3.21.0+verrou-dev 
CMD source /home/valgrind-3.21.0+verrou-dev/build/env.sh

ENV PATH=/home/valgrind-3.21.0+verrou-dev/build/bin:${PATH}
ENV PYTHON_PREFIX=/home/valgrind-3.21.0+verrou-dev/build
ENV PYTHONPATH=/home/valgrind-3.21.0+verrou-dev/build/lib/python3.8/site-packages:${PYTHONPATH}
ENV MANPATH=/home/valgrind-3.21.0+verrou-dev/build/share/man:${MANPATH}
ENV CPATH=/home/valgrind-3.21.0+verrou-dev/build/include:${CPATH}
ENV VERROU_COMPILED_WITH_FMA=yes
ENV VERROU_COMPILED_WITH_QUAD=yes

ENTRYPOINT [ "/bin/bash" ]







