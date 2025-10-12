# PocketBase Backend for TODO Dashboard

This repository contains the PocketBase backend server for the TODO Dashboard application.

## Deployment

This repository is automatically deployed to Railway when changes are pushed to the main branch.

## Configuration

- **Railway Configuration**: `railway.json` specifies Dockerfile-based deployment
- **Dockerfile**: `Dockerfile.pocketbase` contains the container build instructions
- **Database Schema**: Migrations in `pb_migrations/` define database structure
- **Database Storage**: Actual data stored in Railway Volume (mounted at `/pb/pb_data`)

## Project Structure

```
todo-dashboard-pocketbase/  # PocketBase backend (separate repository)
├── .env.local
├── Dockerfile.pocketbase   # Railway deployment configuration
├── railway.json
├── README.md
├── DEPLOYMENT_GUIDE.md
├── pb_migrations/          # Database schema migrations
│   ├── 1755958549_created_dashboards.js
│   ├── 1755963240_updated_dashboards.js
│   └── 1755963564_created_widgets.js
└── pocketbase/             # PocketBase executable and files
    ├── pocketbase          # Linux executable
    └── pb_data/            # Runtime database (Railway Volume, not in git)
        ├── data.db         # User data, dashboards, widgets
        ├── logs.db         # Application logs
        └── types.d.ts      # Auto-generated TypeScript types

Railway Deployment Architecture:
┌─────────────────────────────────────────────────────────────┐
│ Railway Service: todo-dashboard-pocketbase                  │
│                                                             │
│ ┌──────────────────┐                ┌────────────────────┐  │
│ │ Docker Container │   Mount Path   │   Railway Volume   │  │
│ │   /pb/pb_data/   │ ◄────────────► │   Persistent Data  │  │
│ │                  │   /pb/pb_data  │   (data.db, logs)  │  │
│ └──────────────────┘                └────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

**Note**: `pb_data/` files in this repository are NOT used in production. Railway uses a separate Volume for persistent data storage.

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