# IRC Server

This project is an implementation of an **IRC (Internet Relay Chat) server** in C++. It allows multiple clients to connect, communicate in channels, and execute various IRC commands.

---

## Features

- **Socket Programming**: Uses sockets and epoll for handling multiple clients simultaneously.
- **Client Authentication**: Clients authenticate using a password, username, and nickname.
- **Channel Management**: Clients can create, join, leave, and manage channels.
- **IRC Commands**: Supports commands like `JOIN`, `NICK`, `PRIVMSG`, `KICK`, `TOPIC`, and more.
- **Bot Functionality**: Includes a bot that provides jokes, the current date, and the number of connected clients.

---


### Key Components

- **`Server`** ([`Server.hpp`](includes/Server.hpp), [`Server.cpp`](src/Server.cpp)): Manages client connections, channels, and command handling.
- **`Client`** ([`Client.hpp`](includes/Client.hpp), [`Client.cpp`](src/Client.cpp)): Represents a connected user and manages their state.
- **`Channel`** ([`Channel.hpp`](includes/Channel.hpp), [`Channel.cpp`](src/Channel.cpp)): Represents an IRC channel and manages its members, operators, and modes.
- **`IRCCommandHandler`** ([`IRCCommandHandler.hpp`](includes/IRCCommandHandler.hpp), [`IRCCommandHandler.cpp`](src/IRCCommandHandler.cpp)): Processes and executes IRC commands.
- **Commands** ([`src/commands/`](src/commands/)): Implements individual IRC commands like `JOIN`, `NICK`, `PRIVMSG`, etc.
- **Utilities** ([`Utilities.hpp`](includes/Utilities.hpp), [`Utilities.cpp`](src/Utilities.cpp)): Provides helper functions like string manipulation.

---

## Supported Commands

| Command   | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `PASS`    | Authenticate the client with a password.                                   |
| `NICK`    | Set or change the client's nickname.                                       |
| `USER`    | Set the client's username.                                                 |
| `JOIN`    | Join a channel or create one if it doesn't exist.                          |
| `PART`    | Leave a channel.                                                           |
| `PRIVMSG` | Send a private message to a user or channel.                               |
| `TOPIC`   | Get or set the topic of a channel.                                         |
| `KICK`    | Remove a user from a channel.                                              |
| `MODE`    | Manage channel modes (e.g., invite-only, topic-protected).                 |
| `INVITE`  | Invite a user to a channel.                                                |
| `WHO`     | List users in a channel.                                                   |
| `QUIT`    | Disconnect from the server.                                                |
| `BOT`     | Interact with the bot (`JOKE`, `DATE`, `CLIENTS`).                         |

---

## How to Build and Run

### Build

Compile the project using the Makefile:
```bash
make
```

### Run

Start the server with a port and password:
```bash
./ircserv <port> <password>
```

### Connect a Client

You can connect to the server using an IRC client like `netcat`, `irssi`, or a custom client.

Example using `netcat`:
```bash
nc localhost <port>
```

Authenticate the client:
```
PASS <password>
USER <username> 0 * <realname>
NICK <nickname>
```

---

## Example Workflow

1. Start the server:
   ```bash
   ./ircserv 6667 default
   ```

2. Connect a client using `netcat`:
   ```bash
   nc localhost 6667
   ```

3. Authenticate the client:
   ```
   PASS default
   USER myuser 0 0 0
   NICK mynick
   ```

4. Join a channel:
   ```
   JOIN #mychannel
   ```

5. Send a message:
   ```
   PRIVMSG #mychannel :Hello, world!
   ```

6. Use the bot:
   ```
   BOT JOKE
   ```

---

## Bot Commands

| Command   | Description                              |
|-----------|------------------------------------------|
| `JOKE`    | Sends a random joke.                    |
| `DATE`    | Sends the current date and time.        |
| `CLIENTS` | Sends the number of connected clients.  |

---


