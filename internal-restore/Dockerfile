FROM python:3.10.4-buster

LABEL Sobolev Andrey

RUN echo "alias rm='rm -i'" >> ~/.bashrc
RUN echo "alias cp='cp -i'" >> ~/.bashrc
RUN echo "alias mv='mv -i'" >> ~/.bashrc
RUN echo "alias ls='ls --color=auto'" >> ~/.bashrc
RUN echo "alias ll='ls -la'" >> ~/.bashrc
RUN echo "alias grep='grep --color=auto'" >> ~/.bashrc
RUN echo "alias egrep='egrep --color=auto'" >> ~/.bashrc
RUN echo "alias fgrep='fgrep --color=auto'" >> ~/.bashrc
RUN echo "alias ports='netstat -tulanp'" >> ~/.bashrc
RUN echo "alias df='df -H'" >> ~/.bashrc
RUN echo "alias du='du -ch'" >> ~/.bashrc

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    gcc && apt-get install -y \  
    libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev libjpeg-dev libfreetype6-dev python-dev libpq-dev python-dev libxml2-dev libxslt-dev postgresql-client git && \
    apt-get install -y libxrender1 libxext-dev fontconfig && \
    pip3 install -U pip setuptools 

WORKDIR /home/

COPY ./internal-restore /home/
RUN pip3 install --upgrade pip

RUN pip3 install -r ./requirements.txt
CMD uvicorn app:app --reload --port 10006


 
