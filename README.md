# 🤯 LMStudio Prompt Queue System

A modular system for local model prompt management and remote prompt execution using LMStudio. It consists of two core components:

1. **LMMQ** - *Local Model Management Queue*  
   Handles **prompt queuing** and **execution on a local PC**.
   
2. **LMRMQ** - *Local Model Remote Management Queue*  
   A **mobile or secondary client app** that syncs prompts and outputs to the LMMQ server.

---

## 🔥 Features

### 🧷 Queue Features (LMMQ & LMRMQ)

- Queue multiple prompts even while others are processing
- Select from available local models (e.g., `llama-3`, `mistral`, `gemma`)
- Model-specific queuing (each prompt is tagged with its selected model)
- Local prompt queue on both PC and mobile
- Offline support for prompt storage and queuing
- UI status indicators for prompts: Queued, Sending, Done
- Retry logic with exponential backoff

### 🌐 Remote Features (LMRMQ & LMMQ)

- Mobile app (LMRMQ) syncs to PC server (LMMQ)
- Bi-directional ping to detect:
  - Server (PC) online status
  - Client (Mobile or PC) connectivity
- Server app (LMMQ) includes:
  - Server + client hybrid (WApp 1)
  - Standalone client-only mode (WApp 2)
- Input and output are saved on the server
- Data is encrypted and synced between server and mobile
- Sync happens automatically when connection is restored
- Prompt data includes input, output, and selected model
- Local encrypted database stores all prompt history on the server
- The **PC server (LMMQ WApp1)** is composed of two compartmentalized apps:
  - A **Server app** for handling prompt execution and syncing
  - A **Client app** for queuing and managing user interaction
- WApp1 integrates these two components natively while keeping them modular
- **WApp2** is a **standalone Client** for Windows that connects to any LMMQ server

---

## ⚙️ Architecture Overview

### 🖥 LMMQ (Local Model Management Queue)

- PC app that serves as both server and client
- Can queue, execute, store, and sync prompts
- Includes two distribution modes:
  - **WApp1**: Full Suite  
    - Contains both **Server** and **Client** as **separate apps**, natively integrated through compartmentalization.
    - Runs in a unified interface, but each module (Server, Client) operates independently in the background.
  - **WApp2**: Client-Only  
    - Lightweight desktop app that connects to an existing LMMQ Server instance (e.g., on another PC).
- Handles queuing, local model execution, encrypted storage, and syncing with remote clients.

### 📱 LMRMQ (Local Model Remote Management Queue)

- Mobile client app
- Sends prompts to the LMMQ server
- Retrieves results and output once synced
- Acts as a remote queue interface for LMMQ

---

## 📒 Example Use Case

1. Open **LMMQ** on your PC and select a local model like `llama-3`.
2. On your mobile device (using **LMRMQ**), enter a prompt and select a model.
3. Press "Send" — the prompt is added to the mobile's local queue.
4. While `Prompt 1` is processing, you can add `Prompt 2` with another model.
5. If offline, prompts are saved locally on the mobile app.
6. Once online:
   - Prompts are automatically sent to LMMQ.
   - The PC executes them using the correct model.
   - LMMQ syncs the output back to LMRMQ.
   - Input/output and model selection are saved in LMMQ’s encrypted database.

---

## ✅ TODO

### 🧷 Queue Tasks

- [ ] Model selection dropdown
- [ ] Prompt input and send functionality
- [ ] Local queue system on both PC and mobile
- [ ] Model-tagged prompt queuing
- [ ] Prompt status indicators ("queued", "sending", "done")
- [ ] Retry logic for failed requests

### 🌐 Remote Sync Tasks

- [ ] Ping system to detect server availability
- [ ] Ping system to detect mobile client availability
- [ ] Offline detection and local prompt storage
- [ ] Encrypted data storage and transmission
- [ ] Sync from server to client (output history)
- [ ] Secure server access (API key or token)
- [ ] Auto-discovery of models from the LMStudio server
- [ ] Dual-mode support in LMMQ: Server+Client (WApp1), Client-only (WApp2)

---

## 📝 Changelog

### v0.0.1 (Concept)
- Defined architecture: LMMQ (server) + LMRMQ (mobile)
- Partitioned features into Queue and Remote sync
- Initial README draft with core functionality
- TODO tracking system established

---

## 🤝 Contributing

Feel free to suggest features, report bugs, or contribute improvements.  
Open an issue or create a pull request with your proposal.

