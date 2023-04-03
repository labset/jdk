FROM maven:3.9.0-amazoncorretto-19


# required for building openjdk in linux environment !
RUN apt-get update \
    && apt-get install -y file autoconf make unzip zip build-essential \
    && apt-get install -y libasound2-dev libcups2-dev libfontconfig1-dev libx11-dev libxext-dev \
    && apt-get install -y libxrender-dev libxrandr-dev libxtst-dev libxt-dev

# required for sake of experimenting in codespaces !
RUN apt-get install -y git ant \
    && echo 'export ANT_HOME=/usr/share/ant' >> ~/.bashrc \
    && git clone https://github.com/jenv/jenv.git ~/.jenv \
    && echo 'export PATH="${HOME}/.jenv/bin:${PATH}"' >> ~/.bashrc \
    && echo 'eval "$(jenv init -)"' >> ~/.bashrc

# Hasnae's openjdk-compiler-workshops \
RUN mkdir -p ~/sources \
    && git clone https://github.com/viqueen/openjdk-compiler-workshops.git ~/sources/openjdk-compiler-workshops
