# Let's Quiz

A real-time multiplayer quiz game built for the **Secure Network Programming** course project.

This project implements a TLS-based client-server quiz system with user authentication, encrypted communication, quiz room management, timed questions, scoring, and ranking.

## Overview

**Let's Quiz** is a terminal-based multiplayer quiz platform.

Users connect to a central server through a TLS connection, register or log in, join the quiz lobby, and solve questions in real time. The server manages connected users, quiz progress, answer validation, score calculation, rankings, and high score records.

## Key Features

- TLS-based client-server communication
- User registration and login
- SHA-256 password hashing
- AES-256-CBC encrypted data storage
- Multiplayer quiz lobby
- Room leader system
- Quiz file upload by leader
- 15-second time limit for each question
- Rank-based score calculation
- Real-time total score and ranking display
- High score management

## Tech Stack

- C
- TCP Socket Programming
- OpenSSL
- TLS
- SHA-256
- AES-256-CBC
- POSIX Threads
- Makefile

## Project Structure

```text
.
├── client/
│   ├── client.c
│   ├── Makefile
│   ├── certificates/
│   │   └── ca.crt
│   └── client_users.db
│
├── server/
│   ├── main.c
│   ├── account.c / account.h
│   ├── client_handler.c / client_handler.h
│   ├── lobby.c / lobby.h
│   ├── quiz.c / quiz.h
│   ├── util.c / util.h
│   ├── Makefile
│   ├── certificates/
│   │   ├── ca.crt
│   │   ├── server.crt
│   │   └── server.key
│   ├── users.db
│   ├── highscores.db
│   └── security_programming.q
│
└── documents/
    ├── 보네프 최종.pdf
    ├── 보네프 최종.pptx
    └── 보네프 프로젝트 패킷 분석 보고서_타조.pdf
```

## Build

### Server

```bash
cd server
make
```

### Client

```bash
cd client
make
```

## Run

### 1. Start the server

```bash
cd server
./server
```

The server listens on port `9999`.

### 2. Start the client

```bash
cd client
./client
```

For local testing, enter:

```text
127.0.0.1
```

## How to Play

1. Start the server.
2. Run at least 3 clients.
3. Register or log in.
4. The first connected user becomes the room leader.
5. The leader selects or uploads a quiz file.
6. The quiz starts when at least 3 users are connected.
7. Each player answers within 15 seconds.
8. Scores and rankings are updated after each question.
9. Final rankings and high scores are displayed at the end.

## Quiz Format

Quiz files contain multiple-choice questions.

```text
question | option1 | option2 | option3 | option4 | correct_answer | difficulty
```

- `correct_answer`: number from 1 to 4
- `difficulty`: number from 1 to 3

## Security Features

- TLS is used to protect communication between client and server.
- User passwords are hashed with SHA-256.
- User data, quiz files, and high score records are encrypted with AES-256-CBC.
- Login validation uses a counter-based hash value to reduce replay risk.

## Documents

For more details, refer to the project documents:

- [Final Report](documents/보네프%20최종.pdf)
- [Final Presentation](documents/보네프%20최종.pptx)
- [Packet Analysis Report](documents/보네프%20프로젝트%20패킷%20분석%20보고서_타조.pdf)

## Course

**Secure Network Programming Project**  
2025
