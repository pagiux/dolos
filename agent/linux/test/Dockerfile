FROM ubuntu:latest
COPY agent /agent

RUN apt update
RUN apt install -y build-essential python3.5 python3.5-dev
RUN chmod +x /agent/agent

CMD ["/bin/bash"]
