FROM nvidia/cuda:11.4.0-base


RUN apt-get update && apt-get install -y --no-install-recommends python3 python3-pip python3-dev llvm llvm-dev
#RUN pip3 install rembg
RUN pip install -i https://mirrors.aliyun.com/pypi/simple/ rembg

ENTRYPOINT ["rembg"]
CMD []
