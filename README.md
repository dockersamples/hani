# Hani (goose in Estonian)

This project sets up [Goose](https://github.com/block/goose) in a containerized environment, powered by the Model runner in Docker Desktop and connecting to the AI Tools Catalog by Docker. 

If you have a Docker Desktop with the Model runner installed, you can run it locally: 

```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -p 7681:7681 olegselajev241/hani
```

Override  the default model selection: 
```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -p 7681:7681 -e GOOSE_MODEL=ai/mistral-nemo:12B-Q4_K_M olegselajev241/hani
```

Prefer tools-aware models, Goose is an MCP client, so giving it access to tools multiplies the usefullness by a lot. 

## Components

- **Goose**: Main application
- **ttyd**: Web terminal interface
- **Docker CLI**: For running socat container to access AI Tools catalog

## Getting Started

### Prerequisites
- Docker

### Setup

1. Clone this repository:
   ```
   git clone https://github.com/shelajev/hani.git
   cd hani
   ```

2. Build and run the container (sets Docker context to default, because it maps socket into container to run other containers)
   ```
   ./build.sh
   ```
3. Open Goose session in the browser: [http://localhost:7681](http://localhost:7681)

## Customization

To customize the Goose container, modify the `Dockerfile` and rebuild:

```
./build.sh
``` 
