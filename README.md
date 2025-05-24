# LMMQ--prompt-Queuing-and-remote-prompt-execution-for-local-llm
# LMRMQ (Local Model Remote Management Queue)
# 📱 LMStudio Prompt Queue App

This app interfaces with an LMStudio server running on a PC. It allows users to select different models (like LLaMA 3), queue prompts, and send them even while others are still processing. Prompts are stored offline when the server is unavailable and automatically sent when the connection is restored.

---

## 🧠 Features

- Select any available model (e.g. `llama-3`, `Gemma`)
- Enter and send multiple prompts in parallel
- Prompts are stacked/queued for processing
- Offline support: prompts and model selections are saved locally
- Automatic re-sending of queued prompts when the server is available
- Bi-directional ping system:
  - Detects if the server (PC) is online
  - Detects if the (mobile/pc) client is online
- Input and output are both saved on the server and synced when client reconnects
- Encrypted data sync between server and client
- The PC server also acts as a client to send/receive data and manage state
- All prompt data (input/output + selected model) is stored in a secure local database on the server

---

## ⚙️ How It Works

### 1. Model Selection

User selects a model from the list (e.g. `llama-3`).

### 2. Prompt Entry

User enters a prompt, selects model and presses "Send". The prompt, along with its associated model, is added to a local queue.

### 3. Queuing System

- Prompts are stored locally with the selected model.
- Multiple prompts can be entered even while previous ones are being processed.
- The app supports switching models between prompts.

### 4. Offline Behavior

- If the app cannot connect to the server, prompts are saved offline.
- The local queue persists until the server is reachable again.
- The server can also operate offline and stores input/output in its own encrypted database.


### 5. Automatic Sync

- When the server (PC) becomes available, the app automatically sends all queued prompts in order.
- Likewise, when the client comes back online, the server syncs saved prompts and outputs back to the client.
- All data transferred is encrypted for security.

### 6. Ping System

- A lightweight **ping** is used to detect if:
  - The server is online
  - The client (mobile device) is reachable

---

## ✅ TODO

- [ ] Model selection dropdown (e.g. `llama-3`, `mistral`, etc.)
- [ ] Prompt input and send functionality
- [ ] Support for sending multiple prompts in parallel
- [ ] Local prompt queue system
- [ ] Offline detection and local storage of prompts
- [ ] Automatic queue flushing when reconnected
- [ ] Ping system to check server availability
- [ ] Ping system to check mobile client availability
- [ ] UI status indicators ("queued", "sending", "done")
- [ ] Retry logic with exponential backoff
- [ ] Secure server access (token/API key support)
- [ ] Auto-discovery of available models from the LMStudio server

---

## 📌 Example Use Case

1. Select `Llama` model  
2. Enter `Prompt 1` and press Send  
3. While `Prompt 1` is processing, enter `Prompt 2` with `mistral` which gets added to the queue
4. If offline, prompt are stored locally with the model  
5. Once online, prompts are sent to the correct models in order
5. Meanwhile, the **server app also saves input/output locally**, waiting for the client to reconnect.
6. Once the connection is restored:
   - The mobile app **automatically sends** all queued prompts to the server.
   - The server **syncs any stored prompt-output history back to the client**.
   - All data is encrypted during sync.

---

## 📝 Changelog

### v0.0.1 (Concept)
- Initial README and project concept defined
- Feature list drafted
- Development TODO list created
- Architectural overview written

---

Let me know if there are any features or techniques to implement. Do a pull request for any further suggestions.
