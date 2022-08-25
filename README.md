# The base image for Cedarhill's projects

## All images

* `freeyeti/cedarhill-dev:python3.10-weasyprint` for development
* `freeyeti/cedarhill-dev:pyinstaller5.3-poetry` for building
* `freeyeti/cedarhill-dev:python3.10-weasyprint-shipment` for production

## Build and push example:

```bash
./build python3.10-weasyprint
docker push freeyeti/cedarhill-dev:python3.10-weasyprint
```
