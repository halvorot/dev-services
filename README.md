# DevServices

:warning: ONLY *broker*, *schema-registry*, and *akhq* is tested and working :warning:
:warning: KTB not working :warning:

> This is derived from the [Confluent cp-all-in-one](https://github.com/confluentinc/cp-all-in-one) repository.

DevServices is a Docker compose project for quick local setup of local development services such as Kafka, AKHQ, MinIO S3, and various databases.

*Services:*

- Kafka in KRaft mode
- Schema Registry
- AKHQ
- Kafka Topology Builder
- Kafka Connect
- ksqlDB Server
- ksql Datagen
- Kafka REST Proxy
- Oracle Database
- MSSQL Database
- MinIO S3 bucket storage

## Usage

### Running DevServices

```
docker compose up -d
```

This command will run the default services.
See [Profiles](#profiles) for information on how to run additional services.

*Default Services:*

- Kafka in KRaft mode
- Schema Registry
- AKHQ
- MinIO S3 bucket storage

### Profiles

If you want to run other services in addition to the default ones, simply add the respective profile. 

| Profile           | Containers                |
|-------------------|---------------------------|
| ktb               | Kafka Topology Builder    |
| kafka-extended    | Additional Kafka Services |
| oracle            | Oracle Database           |
| mssql             | MSSQL Database            |

Example:

```
docker compose --profile mssql up -d
```

### Stopping DevServices

```
docker compose down -v
```

Remember to also add the started profiles to your command, e.g. `docker compose --profile mssql down -v`

> :warning: Adding the `-v` flag will delete all volumes created by DevServices.
If you want to persist the data in the databases and MinIO S3 buckets, remove the `-v` flag from the command.