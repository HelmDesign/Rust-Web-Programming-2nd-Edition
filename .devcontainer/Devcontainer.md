# DevContainer Setup for Rust Web Programming

This DevContainer configuration provides a complete development environment for the Rust Web Programming 2nd Edition repository with all necessary tools pre-installed.

## 📋 Included Tools & Components

- **Rust** - Latest stable version with rustfmt, clippy, and essential cargo plugins
- **Node.js** - LTS version with npm
- **Python 3** - Latest version with pip, pytest, black, and flake8
- **Docker** - Docker CLI and docker-compose for containerized deployments
- **Terraform** - Infrastructure as Code tool
- **Postman CLI** - API testing and automation
- **Additional tools** - Git, jq, build-essential, and more

## 🚀 Quick Start

### Prerequisites

1. **VS Code** - [Download](https://code.visualstudio.com/)
2. **Dev Containers Extension** - Install from VS Code extensions marketplace
3. **Docker Desktop** - [Download](https://www.docker.com/products/docker-desktop/)
   - Ensure Docker is running before opening the devcontainer

### Setup Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/HelmDesign/Rust-Web-Programming-2nd-Edition.git
   cd Rust-Web-Programming-2nd-Edition
   ```

2. **Create `.devcontainer` directory:**
   ```bash
   mkdir -p .devcontainer
   ```

3. **Copy these files into `.devcontainer/`:**
   - `Dockerfile`
   - `devcontainer.json`
   - `.dockerignore` (optional, goes in root)

4. **Open in VS Code:**
   ```bash
   code .
   ```

5. **Reopen in Container:**
   - Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
   - Type "Dev Containers: Reopen in Container"
   - VS Code will build the Docker image and start the container

6. **Wait for initialization:**
   - The container will run the `postCreateCommand` to verify all tools are installed
   - You'll see version outputs in the terminal

## 📦 Pre-installed VS Code Extensions

### Rust Development
- `rust-analyzer` - Rust language support
- `CodeLLDB` - Debugging support
- `Crates` - Dependency management
- `Dependi` - Dependency tracking

### Web Development
- `ESLint` - JavaScript linting
- `Prettier` - Code formatter
- `JavaScript Snippets`

### Python Development
- `Python` - Core Python support
- `Pylance` - Language server
- `Debugpy` - Debugging
- `Black` - Code formatter
- `Ruff` - Fast Python linter

### DevOps & Infrastructure
- `Docker` - Container support
- `Terraform` - Infrastructure as Code
- `REST Client` - API testing

### General Tools
- `GitLens` - Git integration
- `GitHub Copilot` - AI code assistance (requires auth)
- `SonarLint` - Code quality
- `Markdown` - Documentation support

## 🔧 Configuration Details

### Port Forwarding
The following ports are automatically forwarded:
- **3000** - Node.js/Default web applications
- **5000** - Python Flask
- **8000** - Python Django
- **8080** - General web services
- **8443** - HTTPS services
- **5432** - PostgreSQL databases
- **6379** - Redis
- **27017** - MongoDB
- **9090** - Prometheus/Grafana

### Environment Variables
- `RUST_LOG=debug` - Rust logging level
- `PYTHONUNBUFFERED=1` - Python unbuffered output
- `NODE_ENV=development` - Node environment

### Mount Points
- SSH keys are mounted for Git operations
- Git config is mounted for credentials
- Docker socket is mounted for Docker-in-Docker capability

## 📝 Common Tasks

### Rust Development
```bash
# Create a new Rust project
cargo new my_project

# Build project
cargo build

# Run with debug logging
RUST_LOG=debug cargo run

# Run tests
cargo test

# Format code
cargo fmt

# Lint with clippy
cargo clippy
```

### Node.js Development
```bash
# Initialize Node project
npm init -y

# Install dependencies
npm install package_name

# Run scripts
npm run dev
```

### Python Development
```bash
# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install packages
pip install package_name

# Run tests
pytest

# Format code
black .

# Lint
flake8 .
```

### Docker Operations
```bash
# Build images
docker build -t my-image .

# Run containers
docker run -d my-image

# Use docker-compose
docker-compose up -d
```

### Terraform
```bash
# Initialize Terraform
terraform init

# Plan infrastructure changes
terraform plan

# Apply changes
terraform apply

# Destroy infrastructure
terraform destroy
```

### Postman API Testing
```bash
# Run Postman collections
postman collection run collection.json
```

## 🔒 Security Notes

1. **SSH Keys** - Your local SSH keys are mounted read-only for Git operations
2. **Git Config** - Your git configuration is available in the container
3. **Non-root User** - Container runs as `devuser` for security
4. **Docker Socket** - Mounted for Docker-in-Docker functionality

## 🆘 Troubleshooting

### Container won't build
- Ensure Docker Desktop is running
- Check internet connection (downloads are needed)
- Rebuild: `Dev Containers: Rebuild Container` command

### Tools not found
- Verify installation: Run `postman --version`, `terraform --version`, etc.
- Rebuild the container if recently added tools

### Port conflicts
- Check if ports are already in use: `lsof -i :PORT_NUMBER`
- Modify port mappings in `devcontainer.json` if needed

### Permission issues
- Run as the dev user (default)
- For Docker: The socket is pre-configured

### Slow performance on Mac/Windows
- Check Docker Desktop settings (CPU, memory allocation)
- Consider using WSL 2 on Windows for better performance
- Cache-mounted volumes help with performance

## 🔄 Updating Dependencies

### Update Rust
```bash
rustup update
```

### Update Node packages
```bash
npm update -g
```

### Update Python packages
```bash
pip install --upgrade pip
```

### Update Terraform
```bash
terraform -install-autocomplete
```

## 📚 Additional Resources

- [VS Code Dev Containers Docs](https://code.visualstudio.com/docs/devcontainers/containers)
- [Rust Book](https://doc.rust-lang.org/book/)
- [Rust Web Programming Resources](https://www.rust-lang.org/what/wg-web/)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Python Documentation](https://docs.python.org/3/)
- [Docker Documentation](https://docs.docker.com/)
- [Terraform Documentation](https://www.terraform.io/docs/)

## 💡 Tips

1. **Customize Extensions** - Edit the extensions list in `devcontainer.json` to match your workflow
2. **Add Environment Variables** - Extend `remoteEnv` section for project-specific variables
3. **VSCode Settings** - Modify the `settings` section for your preferred formatting and linting
4. **Add Features** - Uncomment the `features` section to use pre-built devcontainer features
5. **Rebuild Often** - If dependencies change, rebuild: `Dev Containers: Rebuild Container`

## ❓ Need Help?

- Check the [VS Code Dev Containers documentation](https://code.visualstudio.com/docs/devcontainers/containers)
- Review individual tool documentation for specific features
- Report issues in the repository