# PocketBase Backend for TODO Dashboard

This repository contains the PocketBase backend server for the TODO Dashboard application.

## Deployment

This repository is automatically deployed to Railway when changes are pushed to the main branch.

## Configuration

- **Railway Configuration**: `railway.json` specifies Dockerfile-based deployment
- **Dockerfile**: `Dockerfile.pocketbase` contains the container build instructions
- **Database**: SQLite database with migrations in `pocketbase/pb_migrations/`

## Local Development

```bash
# Download and extract PocketBase
wget https://github.com/pocketbase/pocketbase/releases/download/v0.22.21/pocketbase_0.22.21_linux_amd64.zip
unzip pocketbase_0.22.21_linux_amd64.zip

# Run PocketBase
./pocketbase serve
```

## Production URLs

- **API**: https://pocketbase-todo-dashboard.up.railway.app
- **Admin Panel**: https://pocketbase-todo-dashboard.up.railway.app/_/