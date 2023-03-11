# week 2  - Distributed Tracing 

## Requird Homework/ Tasks

### Launch the repo within HoneyComb

You'll need to grab the API key from your honeycomb account:

```
export HONEYCOMB_API_KEY="HALnMmBEtUlDkj7VBiPoeD"
gp env HONEYCOMB_API_KEY="HALnMmBEtUlDkj7VBiPoeD"

export HONEYCOMB_SERVICE_NAME="Cruddur"
gp env HONEYCOMB_SERVICE_NAME="Cruddur"

```

Add teh following Env Vars to backend-flask in docker compose

```
OTEL_EXPORTER_OTLP_ENDPOINT: "https://api.honeycomb.io"
OTEL_EXPORTER_OTLP_HEADERS: "x-honeycomb-team=${HONEYCOMB_API_KEY}"
OTEL_SERVICE_NAME: "${HONEYCOMB_SERVICE_NAME}"

```

Install these packages to instrument a Flask app with OpenTelemetry:

```
pip install opentelemetry-api \
    opentelemetry-sdk \
    opentelemetry-exporter-otlp-proto-http \
    opentelemetry-instrumentation-flask \
    opentelemetry-instrumentation-requests
```    
