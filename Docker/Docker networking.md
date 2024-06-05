## [Published ports](https://docs.docker.com/network/#published-ports)

By default, when you create or run a container using `docker create` or `docker run`, the container doesn't expose any of its ports to the outside world. Use the `--publish` or `-p` flag to make a port available to services outside of Docker. This creates a firewall rule in the host, mapping a container port to a port on the Docker host to the outside world. Here are some examples:

| Flag value                      | Description                                                                                                                                             |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-p 8080:80`                    | Map port `8080` on the Docker host to TCP port `80` in the container.                                                                                   |
| `-p 192.168.1.100:8080:80`      | Map port `8080` on the Docker host IP `192.168.1.100` to TCP port `80` in the container.                                                                |
| `-p 8080:80/udp`                | Map port `8080` on the Docker host to UDP port `80` in the container.                                                                                   |
| `-p 8080:80/tcp -p 8080:80/udp` | Map TCP port `8080` on the Docker host to TCP port `80` in the container, and map UDP port `8080` on the Docker host to UDP port `80` in the container. |
