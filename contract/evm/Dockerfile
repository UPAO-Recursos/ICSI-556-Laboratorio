# Use an official Golang runtime as a base image
FROM golang:1.16-alpine

# Set the working directory in the container
WORKDIR /go-ethereum

# Clone the go-ethereum repository
RUN apk add --no-cache git && \
  git clone --branch v1.11.17 --depth 1 https://github.com/ethereum/go-ethereum.git .

# Install dependencies and build Geth
RUN make geth

# Expose the necessary ports
EXPOSE 8545 8546 30303 30303/udp

# Run Geth when the container starts
CMD ["geth", "--http", "--http.addr", "0.0.0.0", "--http.port", "8545", "--http.api", "eth,net,web3,personal"]


# docker build -t ethereum-node .
# docker run -d --name ethereum-node -p 8545:8545 -p 30303:30303 ethereum-node