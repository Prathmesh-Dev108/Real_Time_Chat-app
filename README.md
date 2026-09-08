# Real-Time Chat Application

A real-time messaging web application built with **Spring Boot** and **WebSocket (STOMP over SockJS)**, allowing multiple users to exchange messages instantly without page refreshes. The frontend features a custom **glassmorphism UI** with a day/night theme toggle and an in-app emoji picker.

## Demo

🎥 https://lnkd.in/p/dxHr4Nh3

## Features

- Instant, two-way message delivery using WebSocket (no polling, no refresh)
- Multiple users can join and chat in the same room simultaneously
- Custom glassmorphism-styled chat UI with smooth animations
- Day / Night theme toggle
- Built-in emoji picker for messages
- Responsive layout built with Bootstrap

## Tech Stack

**Backend (Server-Side)**
- Spring Boot
- Spring WebSocket
- Spring Messaging (STOMP Protocol)
- Thymeleaf

**Frontend (Client-Side)**
- Thymeleaf
- JavaScript (ES6)
- SockJS
- STOMP.js
- HTML / CSS
- Bootstrap

**Development & Infrastructure**
- Maven

## How It Works

1. The client establishes a WebSocket connection to the server via **SockJS** at the `/chat` endpoint.
2. **STOMP.js** is used on top of this connection to send and subscribe to messages using the STOMP messaging protocol.
3. When a user sends a message, it's published to the `/app/sendMessage` destination.
4. The Spring Boot backend (`@MessageMapping`) receives it and broadcasts it to all subscribed clients via `/topic/messages` (`@SendTo`).
5. Every connected client receives the message instantly and renders it in the chat window.

## Project Structure

```
src/
 └── main/
     ├── java/com/chat/application/
     │    ├── controller/
     │    │    └── ChatController.java      # WebSocket message mapping
     │    ├── config/
     │    │    └── WebSocketConfig.java      # STOMP endpoint & broker config
     │    └── model/
     │         └── ChatMessage.java          # Message model (sender, content)
     └── resources/
          └── static/
               └── index.html                # Chat UI (HTML/CSS/JS)
```

## Getting Started

### Prerequisites
- Java 17+ (or your configured JDK version)
- Maven

### Run Locally

```bash
# Clone the repository
git clone https://github.com/Prathmesh-Dev108/<Real_Time_Chat-app>.git
cd <Real_Time_Chat-app>

# Run the application
mvn spring-boot:run
```

The app will start on:

```
http://localhost:8080/chat
```

Open this URL in two or more browser tabs/windows to simulate multiple users chatting in real time.

## Screenshots

| Night Theme | Day Theme |
|---|---|
| <img width="937" height="441" alt="Screenshot 2026-09-08 113745" src="https://github.com/user-attachments/assets/64cf4292-ffdf-4f80-8264-ba884b069673" />
 | <img width="944" height="432" alt="Screenshot 2026-09-08 113828" src="https://github.com/user-attachments/assets/d4dcaccd-cb2a-47eb-8e40-00f03cd4c96e" />
 |

## Appraoch Roadmap

- **Landing page** — a proper homepage introducing the app before users enter a chat room
- **Private rooms** — users can create and join password/link-protected rooms instead of one shared global chat
- **Global video chat portal** — a stranger-matching feature (Omegle-style) letting users video call and meet new people from around the world
- **Authentication** — sign in with Google (OAuth 2.0) or register with an email/password account
- Persist chat history in a database (e.g., MySQL/PostgreSQL)
- User profile support (display name, avatar)
- Typing indicators and an online user list
- Deploy to a cloud platform (Render/Railway/AWS)

## Author

**Prathmesh Santosh Ausarkar**
- LinkedIn: [prathmesh-ausarkar](https://www.linkedin.com/in/prathmesh-ausarkar-6617b9374)
- GitHub: [Prathmesh-Dev108](https://github.com/Prathmesh-Dev108)

## License

This project is open source and available for learning purposes.
