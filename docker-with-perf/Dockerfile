FROM eager:2.4.4 as build

RUN apt-get update && apt-get install git build-essential -y

RUN git clone https://github.com/torvalds/linux.git /src

WORKDIR /src

ARG LINUX_KERNEL_VERSION v5.17
RUN apt-get update && apt-get install flex bison -y
RUN git checkout $LINUX_KERNEL_VERSION && cd tools/perf && ls -l && make O=/tmp/ && ls /tmp/

RUN rm -rf /src
WORKDIR /tmp

############################################################
FROM eager:2.4.4
# RUN apt-get install libpython3.7 -y
COPY --from=build /tmp/perf /usr/bin/perf


