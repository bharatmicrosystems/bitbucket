# bitbucket
## Quick Start
```
git clone https://github.com/bharatmicrosystems/bitbucket.git
cd bitbucket
kubectl apply -f bitbucket.yaml
```

This would perform the following steps

Create a persistent volume called bitbucket-pv-volume with a path to /kubevolumes/bitbucket_data. This would ensure that the bitbucket-data is persisted on disk even if the bitbucket container goes down. The disk is replicated across all the nodes so the container can be scheduled to any of the nodes in the cluster

Create a persistent volume claim called bitbucket-pv-claim which binds with bitbucket-pv-volume

Create the bitbucket deployment which contains a reference to the official bitbucket container provided by atlassian and the /bitbucket-data volume mounted to bitbucket-pv-claim.

Create a cluster IP service to expose the bitbucket UI and SSH ports to the kubernetes cluster

Create an ingress service to expose the bitbucket UI port to the outside world on bitbucket.example.com on port 80 and

Create a NodePort service to expose bitbucket.example.com on port 8000 for ssh.

## Further setup
Access Bitbucket from the browser and follow on-screen instructions.

When prompted for choosing the type of configuration, choose "Configure everything myself"

In the database-configuration choose my own database, use database PostgreSQL (Ensure that you have already setup postgres by using https://github.com/bharatmicrosystems/postgres.git)

1. Hostname - postgres-service
2. Port - 5432
3. Database - bitbucketdb
4. User - bitbucketdbuser

Forward and paste the license key
