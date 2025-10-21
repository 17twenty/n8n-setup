# n8n Deployment

This is a modernised version of the n8n Deployment such that we can a) run locally and b) deploy to AWS ECS.

What we did to get here from the original provided is as follows:

| Step | What to Do                                          | Why                      |
| ---- | --------------------------------------------------- | ------------------------ |
| 1    | Strip out Traefik, `depends_on`, and `links`        | Simplify for ECS         |
| 2    | Replace Postgres container with RDS                 | Managed database         |
| 3    | Optional Redis (local or ElastiCache)               | If using queue mode      |
| 4    | Bind-mount `/home/node/.n8n` locally                | For quick testing        |
| 5    | Use EFS mount in ECS for persistence                | Same path in container   |
| 6    | Use ALB for HTTPS                                   | Replace Traefik          |
| 7    | Run separate ECS service for worker (if queue mode) | Standard scaling pattern |

## Deployment Steps

Locally - make sure your .env files is setup (copy the .env.example if needed)

```bash
$ # Up
$ mkdir -p ./data/n8n ./data/files
$ docker compose up -d
$ # Down
$ docker compose down
```

ECS:

```bash
TBD
```
