FROM golang:1.9.0
MAINTAINER talib.man.united@gmail.com

RUN wget https://github.com/Masterminds/glide/releases/download/v0.12.3/glide-v0.12.3-linux-amd64.tar.gz && \
  tar xzvf glide-v0.12.3-linux-amd64.tar.gz && \
  cp linux-amd64/glide /go/bin/glide && \
  rm -r linux-amd64 && rm glide-v0.12.3-linux-amd64.tar.gz

# Install dep
RUN go get github.com/golang/dep/cmd/dep

# Install Ginkgo and Gomega
RUN go get github.com/onsi/ginkgo/ginkgo
RUN go get github.com/onsi/gomega

# Install Node.js
RUN apt-get install --yes curl
RUN curl --silent --location https://deb.nodesource.com/setup_8.x | bash -
RUN apt-get install --yes nodejs
RUN apt-get install --yes build-essential

# Install libfontconfig1 & zip
RUN apt-get install -y libfontconfig && apt-get install zip -y

# Install Yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
  && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

RUN curl --insecure -L "https://packages.cloudfoundry.org/stable?release=linux64-binary&source=github" | tar -zx
# ...move it to /usr/local/bin or a location you know is in your $PATH
RUN mv cf /usr/local/bin
RUN cf --version



