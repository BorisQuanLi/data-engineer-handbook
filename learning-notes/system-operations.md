# System Operations

## Checking PostgreSQL Services

To check the status of PostgreSQL services on your machine, you can use the `systemctl` command. This command will list all PostgreSQL services and their statuses.

Open your terminal and run the following command:

```sh
systemctl list-units --type=service | grep postgresql
```

You should see an output similar to this:

```sh
● postgresql.service                                     loaded failed       failed             PostgreSQL RDBMS
  postgresql@14-main.service                             loaded active       running            PostgreSQL Cluster 14-main
```

This output indicates that one PostgreSQL service is running (`postgresql@14-main.service`), while another service (`postgresql.service`) has failed.
