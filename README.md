# addressr

Free Australian Address Validation, Search and Autocomplete

## Overview

This server was generated by the [swagger-codegen](https://github.com/swagger-api/swagger-codegen) project. By using the [OpenAPI-Spec](https://github.com/OAI/OpenAPI-Specification) from a remote server, you can easily generate a server stub.

### Running the server

To run the server, run:

```
npm start
```

To view the Swagger UI interface:

```
open http://localhost:8080/docs
```

This project leverages the mega-awesome [swagger-tools](https://github.com/apigee-127/swagger-tools) middleware which does most all the work.

## System requirements

Will try with digital ocean using 2GB and 3GB instances via a docker-compose. See what happens 🤷‍♂️.

### Elastic Search:

1.375GiB mem

### Mongo DB

> Changed in version 3.2: Starting in MongoDB 3.2, the WiredTiger internal cache, by default, will use the larger of either:
>
> 60% of RAM minus 1 GB, or
> 1 GB.

On 8GiB host it ended up using 3GiB (38.24%). Need to try constraining this to find the lower limit.

### Loader

~ 752MB (while loading Victoria)

- this is prob because we keep all the street localities and localities in memory
- we could reduce this by putting them in mongo, but that could slow down the load times 🤷‍♂️

### API Server

~

## To Do

[x] Add search API

- [x] Index docs and create search logic
- [x] use papaparse chunks for indexing to reduce memory footprint
- [x] Expose search logic
- [x] implement pagination
      [x] API to get the full structured address
      [ ] start up process. Have the API/Server component separate to the loader component.
- [x] server start script
- [x] loader start script
- [ ] detangle loader and starter
- [ ] server docker image
- [ ] loader docker image
- [ ] docker compose script
      [x] Figure out why search with < 3 chars is giving dodgy results - it's because the min ngram is 3
      [ ] Play around with min ngrams less than 3 and either reduce min ngram or set min length on q param
      [ ] Improve search response time
- was approx 2.7s during data load
- might be less when load isn't happening
  [ ] auth0 integration (to run the components, you need to provide credentials)
  [ ] telemetry capture
  [ ] GA the beta
  [ ] update ES client

### Premium options?

[ ] add highlights to search results
[ ] Aliases
[ ] Geo
[ ] Lowercase
