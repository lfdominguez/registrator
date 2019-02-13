# Registrator

Service registry bridge for Docker (forked from gilderlabs).

[![Docker pulls](https://img.shields.io/docker/pulls/lfdominguez/registrator.svg)](https://hub.docker.com/r/lfdominguez/registrator/)
<br /><br />

Registrator automatically registers and deregisters services for any Docker
container by inspecting containers as they come online. Registrator
supports pluggable service registries, which currently includes
[Consul](http://www.consul.io/).

## Getting Registrator

Get the latest release, master, or any version of Registrator via [Docker Hub](https://registry.hub.docker.com/u/lfdominguez/registrator/):

	$ docker pull lfdominguez/registrator:latest

## Using Registrator

Typically, running Registrator looks like this:

    $ docker run -d \
        --name=registrator \
        --net=host \
        --volume=/var/run/docker.sock:/tmp/docker.sock \
        lfdominguez/registrator:latest \
          -ip-internal-mask=172.16.0.0/24 \
          -ip-external-mask=172.16.1.0/24 \
          consul://localhost:8500

## CLI Options
```
Usage of /bin/registrator:
  /bin/registrator [options] <registry URI>

  -ip-internal-mask: IP Internal for ports mapped to the host
  -ip-external-mask: IP External for ports mapped to the host
  -cleanup=false: Remove dangling services
  -deregister="always": Deregister exited services "always" or "on-success"
  -internal=false: Use internal ports instead of published ones
  -ip="": IP for ports mapped to the host
  -resync=0: Frequency with which services are resynchronized
  -retry-attempts=0: Max retry attempts to establish a connection with the backend. Use -1 for infinite retries
  -retry-interval=2000: Interval (in millisecond) between retry-attempts.
  -tags="": Append tags for all registered services
  -ttl=0: TTL for services (default is no expiry)
  -ttl-refresh=0: Frequency with which service TTLs are refreshed
```

## Contributing

Pull requests are welcome! We recommend getting feedback before starting by
opening a [GitHub issue](https://github.com/lfdominguez/registrator/issues).

## Thanks

To [registrator](https://github.com/gliderlabs/registrator)

Big thanks to Weave for sponsoring, Michael Crosby for
[skydock](https://github.com/crosbymichael/skydock), and the Consul mailing list
for inspiration.

## License

MIT
