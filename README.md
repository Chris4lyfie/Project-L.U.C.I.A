# Project L.U.C.I.A.

> One-line description of what your project does

## Team

| Name | GitHub | Email |
|------|--------|-------|
| Name 1 | [@Chris4lyfie](https://github.com/Chris4lyfie) | christianmichael.villanueva@sjsu.edu |
| Name 2 | [@ling-tang0922](https://github.com/ling-tang0922) | ling.tang@sjsu.edu |
| Name 3 | [@Memekushi](https://github.com/Memekushi) | ethanaelgrimares@sjsu.edu |
| Name 4 | [@noel-tem](https://github.com/noel-tem) | noel.temores@sjsu.edu |

**Advisor:** [Professor Wencen Wu]

---

## Problem Statement

Navigation without external infrastructure in high paced non static environments remains a significant challenge for autonomous systems. Indoor settings like hospitals, warehouses, and restaurants contain constantly changing obstacles like people, equipment, and temporary structures. Many existing solutions rely on GPS and known infrastructure. Introducing new variables into the environment increases the risk of unsafe navigation, and the possibility of personel injury. 

## Solution

Real-time environment mapping utilizing 3-D liDAR scanning. Our system will continuously generate and update a 3-D spatial map while in motion. It will also integrate with AI assisted object recognition enabling navigation in dynamic environments.

### Key Features

- Real-time three dimensional spatial reconstruction using liDAr to produce point clouds during operation.
- Fully autonomous rover navigation utilizing data gathered from mapping. This includes path planning, localization and obstacle avoidance.
- Wireless data communication subsystem for transmitting mapping data and system status to a remote control system.

---

## Demo

[Link to demo video or GIF]

**Live Demo:** [URL if deployed]

---

## Screenshots

| Feature | Screenshot |
|---------|------------|
| [Feature 1] | ![Screenshot](docs/screenshots/feature1.png) |
| [Feature 2] | ![Screenshot](docs/screenshots/feature2.png) |

---

## Tech Stack

| Category | Technology |
|----------|------------|
| Frontend | |
| Backend | |
| Database | |
| Deployment | |

---

## Getting Started

### Prerequisites

- [Prerequisite 1] v.X.X+
- [Prerequisite 2] v.X.X+

### Installation

```bash
# Clone the repository
git clone https://github.com/[org]/[repo].git
cd [repo]

# Install dependencies
[install command]

# Set up environment variables
cp .env.example .env
# Edit .env with your values

# Run database migrations (if applicable)
[migration command]
```

### Running Locally

```bash
# Development mode
[dev command]

# The app will be available at http://localhost:XXXX
```

### Running Tests

```bash
[test command]
```

---

## API Reference

<details>
<summary>Click to expand API endpoints</summary>

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/resource` | Get all resources |
| GET | `/api/resource/:id` | Get resource by ID |
| POST | `/api/resource` | Create new resource |
| PUT | `/api/resource/:id` | Update resource |
| DELETE | `/api/resource/:id` | Delete resource |

</details>

---

## Project Structure

```
.
├── [folder]/           # Description
├── src/                # Source code files
├── tests/              # Test files
├── docs/               # Documentation files
└── README.md
```

---

## Contributing

1. Create a feature branch (`git checkout -b feature/amazing-feature`)
2. Commit your changes (`git commit -m 'Add amazing feature'`)
3. Push to the branch (`git push origin feature/amazing-feature`)
4. Open a Pull Request

### Branch Naming

- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation updates
- `refactor/` - Code refactoring

### Commit Messages

Use clear, descriptive commit messages:
- `Add user authentication endpoint`
- `Fix database connection timeout issue`
- `Update README with setup instructions`

---

## Acknowledgments

- [Resource/Library/Person]
- [Resource/Library/Person]

---

## License

This project is licensed under the <FILL IN> License - see the [LICENSE](LICENSE) file for details.

---

*CMPE 195A/B - Senior Design Project | San Jose State University | Spring 2026*
