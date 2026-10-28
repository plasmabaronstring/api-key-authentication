

![Header](https://capsule-render.vercel.app/api?type=waving&color=0:1A2A6C,100:B21F3D&height=220&section=header&text=Api%20Key%20Authentication&fontSize=60&fontColor=ffffff&animation=twinkling&fontAlignY=35&desc=Fortify%20Your%20Rest%20Apis%20With%20Military%20Grade%20Security&descAlignY=55&descSize=20)

<div align="center">

![Version](https://img.shields.io/badge/version-3.4.0-B21F3D?style=for-the-badge&logo=git&logoColor=white)
![Downloads](https://img.shields.io/badge/downloads-97.1K-1A2A6C?style=for-the-badge&logo=download&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-FFD700?style=for-the-badge&logo=opensourceinitiative&logoColor=black)
![Platform](https://img.shields.io/badge/platform-node.js%20%7C%20python%20%7C%20go-00E676?style=for-the-badge&logo=javascript&logoColor=black)

</div>

---

## 🔐 The Gold Standard Of API Security

Every modern application relies on APIs to connect clients, servers, and third-party services. However, leaving your API endpoints exposed is a catastrophic security risk. **Api Key Authentication** is a production-ready, open-source framework that provides a robust, scalable, and highly secure method for generating, validating, and managing API keys.

Unlike basic Basic-Auth or raw bearer tokens, this framework implements a sophisticated multi-tiered security model. It handles key generation using cryptographically secure random number generators, stores keys as hashed values (bcrypt) to prevent database leaks, and supports granular rate limiting and scope-based permissions.

This repository is designed for backend developers who need to secure their microservices, SaaS platforms, or internal tools quickly. It includes pre-built middleware for Express.js, FastAPI, and Gin (Go), allowing you to drop it into your existing codebase in minutes. It also includes a full administrative dashboard to revoke keys, monitor usage, and generate new credentials.

<img width="1920" height="1080" alt="574347a-API_key_auth" src="https://github.com/user-attachments/assets/3d1d8822-578c-4eaa-b18e-a27bbe86ad23" />


---

## ✨ Core Features

| Feature | Description |
|---------|-------------|
| 🔑 **Secure Key Generation** | Uses `crypto` and `bcrypt` to generate and hash keys |
| 🛡️ **Scope-Based Access** | Assign specific permissions (e.g., `read:users`, `write:posts`) |
| ⚡ **Rate Limiting** | Built-in Redis-backed rate limiter per API key |
| 📊 **Usage Analytics** | Track which keys are making requests and how often |
| ⏳ **Key Expiration** | Set automatic expiration dates for temporary keys |
| 🌐 **Multi-Framework Support** | Pre-built middleware for Node, Python, and Go |
| 📱 **Admin Dashboard** | A sleek UI to manage your API ecosystem |
| 🐳 **Dockerized** | One-command deployment for the entire stack |

---

## 🚀 Quick Setup

To run the authentication server locally, you will need Node.js 18+, PostgreSQL, and Redis. 

```bash
# Clone the repository
git clone https://github.com/your-username/api-key-authentication.git

# Navigate into the directory
cd api-key-authentication

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your database and Redis credentials

# Run the database migrations
npm run migrate

# Start the server
npm run start
```

Once the server is running, open your browser and navigate to `http://localhost:3000/dashboard`. Log in with the default admin credentials, and you can immediately generate your first API key. Copy the key (it is only shown once), and use it in your client requests via the `x-api-key` header.

---

<div align="center">

### 🔗 Ready to secure your API?

[![Get Framework](https://img.shields.io/badge/🔐_GET_FRAMEWORK-1A2A6C?style=for-the-badge&logoColor=white)](https://share.google/ijHD93RzmAOooZbUR)

</div>

---

## 🧠 How The Security Architecture Works

Security is not an afterthought; it is baked into the core of this framework. When a client creates an API key, the server generates a random 32-byte string. It returns the plain text key to the client but stores only the bcrypt hash in the database. If a hacker breaches your database, they cannot reverse the hash to get the original keys.

When a client makes a request, they include the key in the `x-api-key` header. The middleware intercepts the request, extracts the key, and compares it against the stored hashes. To make this process fast, the framework uses a two-step lookup: it stores a fast SHA-256 hash as an index to find the correct bcrypt hash. This prevents the server from having to run bcrypt (which is intentionally slow) on every single database record.

For authorization, the middleware checks the `scopes` array attached to the key. If the route requires `write:posts` and the key only has `read:posts`, the request is rejected with a `403 Forbidden`. The rate limiter then checks Redis to ensure the key hasn't exceeded its allowed requests per minute.

---

<div align="center">

### ⚙️ Need a detailed configuration guide?

[![Setup Guide](https://img.shields.io/badge/📖_VIEW_SETUP_GUIDE-B21F3D?style=for-the-badge&logoColor=white)](https://share.google/ijHD93RzmAOooZbUR)

</div>

---

## 🛠️ Tech Stack

<div align="center">

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

</div>

---

## 🤝 Community & Contributing

API security is a constantly evolving challenge. If you have found a vulnerability, improved the hashing logic, or want to add support for a new language, we welcome your contributions!

1. **Fork** the repository.
2. **Create** your feature branch (`git checkout -b feature/new-middleware`).
3. **Commit** your changes (`git commit -m 'Add new middleware'`).
4. **Push** to the branch (`git push origin feature/new-middleware`).
5. **Open** a Pull Request.

Please read our `CONTRIBUTING.md` for detailed coding standards and security guidelines. We also have an active Discord server where you can ask for help with integration, discuss the latest security threats, and share your API architecture.

---

## 📬 Contact & Support

- 💬 **Discussions:** Join the conversation in the GitHub Discussions tab.
- 🐛 **Issues:** Found a bug? Let us know via the Issues tracker.
- 📧 **Email:** Reach out directly at support@apikey-auth.dev.

---

<div align="center">

### ⭐ If this framework secures your app, give it a star! ⭐

[![Star](https://img.shields.io/badge/⭐_STAR_THIS_REPO-FFD700?style=for-the-badge&logo=github&logoColor=black)](https://github.com/your-username/api-key-authentication)

---

### 🚀 Start securing your API today

[![Get Started](https://img.shields.io/badge/🚀_GET_STARTED_GUIDE-00E676?style=for-the-badge&logoColor=black)](https://share.google/ijHD93RzmAOooZbUR)

<sub>Crafted with precision and ❤️ by the Api Key Authentication community</sub>

![Footer](https://capsule-render.vercel.app/api?type=waving&color=0:B21F3D,100:1A2A6C&height=120&section=footer)

</div>
