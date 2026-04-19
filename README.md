# PairPad

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-ISC-green.svg)
![React](https://img.shields.io/badge/frontend-React%2019-61dafb?logo=react)
![Node](https://img.shields.io/badge/backend-Node.js-339933?logo=node.js)
![Socket.io](https://img.shields.io/badge/realtime-Socket.io-010101?logo=socket.io)

PairPad is a high-performance, real-time collaborative code editor designed for seamless pair programming and remote technical interviews. Built with the power of **Yjs** for conflict-free data synchronization and the **Monaco Editor** for a VS Code-like experience, PairPad ensures that multiple developers can code together in real-time without sync conflicts.

[Features](#features) • [Tech Stack](#tech-stack) • [Architecture](#architecture) • [Getting Started](#getting-started) • [Deployment](#deployment)

---

## 🚀 Features

-   **Real-time Collaboration**: Multi-user editing powered by CRDTs (Conflict-free Replicated Data Types) via Yjs.
-   **Professional Editor**: Integrated with Monaco Editor, providing syntax highlighting, IntelliSense, and a familiar coding environment.
-   **Low Latency**: WebSocket-based communication using Socket.io for near-instant updates.
-   **Responsive Design**: Modern UI built with Tailwind CSS 4.0 for a clean, distraction-free experience.
-   **Dockerized**: Ready for containerized deployment with a pre-configured Dockerfile.

---

## 🛠 Tech Stack

### Frontend
-   **Framework**: React 19 (Vite-powered)
-   **Editor**: Monaco Editor (`@monaco-editor/react`)
-   **Shared Types**: Yjs
-   **Binding**: `y-monaco` (Connects Yjs to Monaco)
-   **Styling**: Tailwind CSS 4.0

### Backend
-   **Runtime**: Node.js
-   **Framework**: Express 5.0
-   **Communication**: Socket.io
-   **Sync Provider**: `y-socket.io` (Server-side Yjs persistence and distribution)

---

## 🏗 Architecture

PairPad utilizes a client-server architecture where the backend acts as a synchronization hub.

1.  **Client-Side**: The Monaco Editor captures user input. `y-monaco` binds the editor state to a local Yjs document.
2.  **Synchronization**: Changes to the local Yjs document are encoded as incremental updates and sent via `y-socket.io` to the server.
3.  **Server-Side**: The Node.js server receives updates and broadcasts them to all other connected clients in the same session, ensuring eventual consistency across all instances.

```text
[User A] <-> [Yjs Doc] <-> [Socket.io] <-> [Express Server] <-> [Socket.io] <-> [Yjs Doc] <-> [User B]
```

---

## 🚦 Getting Started

### Prerequisites
-   **Node.js**: v18.x or higher
-   **npm**: v9.x or higher

### Installation

1.  **Clone the repository**
    ```bash
    git clone https://github.com/shukla-vivek008/PairPad.git
    cd PairPad
    ```

2.  **Setup Backend**
    ```bash
    cd Backend
    npm install
    ```

3.  **Setup Frontend**
    ```bash
    cd ../Frontend
    npm install
    ```

### Running the Application

1.  **Start the Backend Server** (Port 3000)
    ```bash
    cd Backend
    npm run dev
    ```

2.  **Start the Frontend Development Server**
    ```bash
    cd Frontend
    npm run dev
    ```
    The application will typically be available at `http://localhost:5173`.

---

## ⚙️ Configuration

### Environment Variables
Create a `.env` file in the `Backend` directory if you wish to override default settings (optional).

| Variable | Description | Default |
|----------|-------------|---------|
| PORT     | Server port | 3000    |

---

## 🐳 Deployment

### Using Docker

PairPad comes with a `dockerfile` for easy deployment.

1.  **Build the image**:
    ```bash
    docker build -t pairpad .
    ```

2.  **Run the container**:
    ```bash
    docker run -p 3000:3000 pairpad
    ```

---

## 🛣 Roadmap
-   [ ] Support for multiple rooms/sessions.
-   [ ] Language selector for Monaco Editor.
-   [ ] Integrated chat system.
-   [ ] Persistence layer (MongoDB/Redis) for saving sessions.
-   [ ] Presence indicators (showing user cursors).

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1.  Fork the Project.
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

---

## 📄 License

Distributed under the **ISC License**. See `LICENSE` for more information.

---

## 📞 Contact

Vivek Shukla - [shukla-vivek008](https://github.com/shukla-vivek008)

Project Link: [https://github.com/shukla-vivek008/PairPad](https://github.com/shukla-vivek008/PairPad)