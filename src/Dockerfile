FROM gnuoctave/octave:5.2.0

COPY . /

# Install Python and Flask
RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip3 install -r /requirements.txt

WORKDIR /usr/share/octave/packages
RUN wget https://sourceforge.net/projects/octave/files/Octave%20Forge%20Packages/Individual%20Package%20Releases/nnet-0.1.13.tar.gz/download -O nnet-0.1.13.tar.gz && \
    octave --eval 'pkg install nnet-0.1.13.tar.gz'

WORKDIR /

EXPOSE 4647

CMD ["python3", "/server.py"]

# Install Octave nnet package
# WORKDIR /usr/share/octave/packages
# RUN wget -O nnet-0.1.13.tar.gz https://octave.sourceforge.io/download.php?package=nnet-0.1.13.tar.gz && \
#     octave --eval 'pkg install nnet-0.1.13.tar.gz'

# WORKDIR /backend

# COPY ./build/exp/forward-neural-networks/simulation/backend /backend

# RUN python3.11 -m venv venv && \
#     . venv/bin/activate && \
#     pip install --upgrade pip && \
#     pip install -r requirements.txt

# EXPOSE 4647


##### original
# FROM httpd:2.4

# # Install required packages
# RUN apt-get update && \
#     apt-get install -y python3.11 python3-pip python3.11-venv octave liboctave-dev wget && \
#     apt-get clean

# # Install Octave nnet package
# WORKDIR /usr/share/octave/packages
# RUN wget -O nnet-0.1.13.tar.gz https://octave.sourceforge.io/download.php?package=nnet-0.1.13.tar.gz && \
#     octave --eval 'pkg install nnet-0.1.13.tar.gz'

# WORKDIR /backend

# COPY ./build/exp/forward-neural-networks/simulation/backend /backend

# RUN python3.11 -m venv venv && \
#     . venv/bin/activate && \
#     pip install --upgrade pip && \
#     pip install -r requirements.txt

# COPY ./build /usr/local/apache2/htdocs/

# RUN echo 'RedirectMatch ^/$ /Introduction.html' >> /usr/local/apache2/conf/httpd.conf

# EXPOSE 80
# EXPOSE 4647

# CMD ["sh", "-c", ". /backend/venv/bin/activate && python /backend/server.py & httpd-foreground"]