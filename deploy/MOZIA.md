# Mozia upstream deployment

This fork preserves Wei-Shaw/sub2api on `main`. Custom deployments use `mozia`.
The ARM64 application image is built from this branch's source, with its commit
recorded in the image tag and OCI revision label. It is not the upstream latest image.

The combined deployment lives in
[mozia-newapi/deploy/mozia](https://github.com/MoziaVerse/mozia-newapi/tree/mozia/deploy/mozia).
Sub2API runs in simple mode as the private account-pool upstream. New API owns
customer-facing authentication and charging. PostgreSQL 18, Redis and application
data have persistent volumes. All credentials remain outside Git.

On the server, this checkout is `/opt/mozia/mozia-sub2api` with origin pointing to
MoziaVerse/mozia-sub2api and upstream pointing to Wei-Shaw/sub2api. Sync upstream
into `main` first, merge `main` into `mozia`, review, rebuild and deploy the new
commit. Preserve backups and the previous image before upgrading.
