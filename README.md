# tsnet-serve
It's like `tailscale serve` but a standalone app that lives on your tailnet. 

A tsnet app that runs a lightweight reverse proxy on your tailnet. Simply specify
a hostname, backend and provide an auth key. The app will appear on your tailnet
as a machine. Tailscale provides all connectivity, the TLS cert and
runs the same reverse proxy as `tailscale serve`. Just open a web browser and point
it to `https://machine.your-tcd.ts.net`.

## Build and run
To build from source and run:

```shell
go run ./main.go -hostname myapp -backend https://localhost:3000
```

## Docker container
```shell
docker run -d \
    --name=tsnet-serve \
    -v /path/to/state:/state \
    -e TSNS_HOSTNAME=<hostname> \
    -e TSNS_BACKEND=<backend> \
    -e TS_AUTHKEY=<auth key> \
    ghcr.io/shayne/tsnet-serve:latest
```

Initial registration requires an [auth key](https://tailscale.com/kb/1085/auth-keys/) to be set via the `TS_AUTHKEY` env var. 


## Contributing

Contributions to this project are welcome. Please feel free to open an issue or submit a pull request if you have any improvements or bug fixes to suggest.


## License

This project is licensed under the [MIT License](LICENSE).
