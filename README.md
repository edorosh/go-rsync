# GO RSync
The app synchronises files between 2 remote data sources. The app may be running 
locally or could be deployed on a cloud environment (k8s, helm).

> The app is in the development

Supported data sources:
* FTP (with TLS)
* Azure Blob Storage

## Run
Copy the .env file into a .local.env file and replace string `PUT_CREDS_HERE` with your data there.

```bash
cp .env .local.env
```

Then build and run the app:

```
go build ./cmd/gorsync
env $(cat .local.env | xargs) ./gorsync
```

## Development
> **PLEASE DO NOT COMMIT THE .env FILE WITH CREDENTIALS**
### Tests
Mocks are generated by [Mockery](https://github.com/vektra/mockery). The tool should be installed locally. Please
refer to [Installation](https://github.com/vektra/mockery#installation) section to have it installed on your dev env.

The following command generates a mock for the interface Downloader in the folder `./internal/mocks`
```
mockery --name=Downloader -dir ./internal/rsyncapp/  --output ./internal/mocks
```

## License
MIT

## TODO
* create chart for artifacthub.io
* add travic-ci
* add codecov
* add godoc.org
* add goreportcard.com