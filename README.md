# Node.js + AWS CLI + Docker CLI Dev Container (Ubuntu 24.04)

This Docker image is based on **Ubuntu 24.04** and provides a lightweight development environment with the following tools pre-installed:

- Node.js 20.x (via NodeSource)
- AWS CLI v2
- Docker CLI
- Essential utilities (curl, wget, unzip, less, etc.)

It is intended for use in development or CI environments where interaction with AWS and Docker is required, along with Node.js tooling (e.g., `npm`, `npx`).

---

## 🧰 Installed Software

| Tool              | Version / Source                            |
|-------------------|---------------------------------------------|
| Ubuntu            | 24.04                                       |
| Node.js           | 20.x (via NodeSource)                       |
| npm               | Latest matching Node.js version             |
| npx               | Included with npm                           |
| AWS CLI           | v2 (via official installer)                 |
| Docker CLI        | Latest stable (via Docker APT repository)   |
| Utilities         | `curl`, `wget`, `gnupg`, `unzip`, `less`, etc. |

---

## 🔧 Usage

### Build the Image

```bash
docker build -t my-dev-env .
```

### Run a Container

```bash
docker run -it --rm my-dev-env
```

You’ll be dropped into a `bash` shell with all tools available.

---

## 🧪 Quick Test Commands

Inside the container, you can verify that everything is working:

```bash
node -v      # Check Node.js version
npm -v       # Check npm version
npx -v       # Check npx version
aws --version  # Check AWS CLI version
docker --version  # Check Docker CLI version
```

---

## 📁 Notes

- This image does **not** include the Docker daemon — only the CLI. To run Docker commands against your host Docker engine (e.g. from inside a CI runner), you need to mount the Docker socket:

```bash
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock my-dev-env
```

- `DEBIAN_FRONTEND=noninteractive` is set to suppress prompts during package installation.

---

## 📄 License

This Dockerfile uses publicly available tools and is intended for internal or personal development use. Review the licenses of each included tool individually if used in production.
