FROM gnuoctave/octave:9.3.0

# Install Python and Flask
RUN apt-get update && apt-get upgrade -y 

# Install python and other packages required to build virtual env
RUN apt-get install python3 -y && \
    apt-get install python3-venv python3-pip -y && \
    python3 -m venv /vlabs/venv/octave_9-3 

# Activate the venv environment
ENV PATH="/vlabs/venv/octave_9-3/bin:$PATH"

COPY . /vlabs

RUN pip3 install -r /vlabs/requirements.txt

# Install octave nnet package
WORKDIR /usr/share/octave/packages
RUN apt-get install mercurial make && \
    hg clone http://hg.code.sf.net/p/octave/nnet octave-nnet && \
    cd octave-nnet && make install

WORKDIR /vlabs

EXPOSE 4647

CMD ["python3", "server.py"]

