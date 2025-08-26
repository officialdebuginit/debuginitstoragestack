# DebugInit Object Storage Stack

A compact object storage service built for MCP A2A interoperability. It offers a clean API for agent to agent exchange, strong consistency for uploads and retrievals, and signed access with policy controls. Run it locally with Docker and explore the prebuilt web UI.

---

## What is in this bundle

* `DebugInitObjectStorage`
  The backend binary.

* `dist`
  The precompiled React frontend.

* `docker-compose.yml`, `Dockerfile.api`, `Dockerfile.ui-static`, `nginx.conf`
  Ready to run with Docker.

* `.env`
  Your server configuration. Create or edit at the project root.

---

## Quick start

1. **Prepare configuration**

Create a `.env` file at the project root. Use strong values in production.

```env
ADMIN_USERNAME=root
ADMIN_API_KEY=change_this_to_a_long_random_value
SIGNING_SECRET=change_this_to_another_long_random_value

HOST=0.0.0.0
BIND_PORT=8080
PUBLIC_BASE_URL=http://0.0.0.0:8080

CORS_ALLOWED_ORIGINS=http://localhost:8081

# Optional tuning
SERVER_WORKERS=3
```

2. **Launch the stack**

From the project root:

```bash
docker compose up -d
```

This starts

* API at `http://localhost:8080`
* UI at `http://localhost:8081`

Data and metadata persist in local folders `./data` and `./obj_meta_db`.

3. **Sign in to the UI**

Open `http://localhost:8081/login`.

* Username: `root`
* Key: the value of `ADMIN_API_KEY` from your `.env`

You will be redirected to the dashboard after successful verification.

---

## Basic testing

* **Dashboard**
  Visit `http://localhost:8081/dashboard` to confirm the session.

* **Upload and media demo**
  Visit `http://localhost:8081/demo` to test image compression, variant generation, and HLS packaging directly in the browser.

* **Settings**
  Visit `http://localhost:8081/settings/media` to review media defaults used by the demo page.


---

## Stop and clean up

```bash
docker compose down
```

Your data remain in `./data` and `./obj_meta_db`. Remove those folders if you want a clean slate.

---

## Creator

Created by **Sanjay Shah**
[https://shahsanjay.com](https://shahsanjay.com)
[https://debuginit.com](https://debuginit.com)

Full documentation is in progress. Linux application integrations are in progress.
