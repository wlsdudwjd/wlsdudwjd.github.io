---
title: Linux TCP chat program
date: 2024-06-26
links:
  - type: site
    url: https://github.com/wlsdudwjd/LinuxProject
tags:
  - Linux
  - Cpp
  - C
  - TCP
  - Chat
 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/ko/%EC%82%AC%EC%A7%84/%EC%B4%88%EB%A1%9D%EC%83%89-%ED%91%9C%EB%A9%B4%EC%97%90-%EA%B5%AC%EA%B2%A8%EC%A7%84-%EB%85%B8%EB%9E%80%EC%83%89-%EC%A2%85%EC%9D%B4-%EC%84%B8-%EC%9E%A5%EC%9D%B4-%EB%85%B8%EB%9E%80%EC%83%89-%EC%A4%84%EC%9D%B4-%EA%B7%B8%EC%96%B4%EC%A7%84-%EC%A2%85%EC%9D%B4%EB%A1%9C-%EB%91%98%EB%9F%AC%EC%8B%B8%EC%97%AC-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4-V5vqWC9gyEU)'
  focal_point: ""
  preview_only: false   

featured: true

share: false

reading_time: false
---

Based on what I learned in my Linux System Programming class, I implemented a simple multi-client TCP chat program as a project.

It was a meaningful experience to directly apply the concepts of C socket communication and multithreading (pthreads). I'd like to summarize the project's structure, core operating principles, and the key takeaways.

## 1. Project Overview
This program is a simple console-based (terminal) chatroom that allows a single server and multiple clients to chat in real-time over the TCP/IP protocol.

**Key Technologies**: C Language, TCP/IP Socket Programming, pthread (Multithreading)

**Core Features**:

- Server: Manages multiple client connections simultaneously.

- Broadcasting: Transmits a message from one client to all other connected clients (except the sender).

- Multi-Chat: Allows multiple users to send and receive messages at the same time.

## 2. Core Architecture: How Concurrency is Achieved
The core challenge of a chat program is handling multiple requests simultaneously. Functions like accept(), recv(), and fgets() are blocking by default. This means the entire program pauses and waits for an operation to complete before moving on.

I used multithreading to solve this problem.

⚙️ **Server: Thread-per-Client Model**
The server needs to handle connection requests and receive messages from multiple clients at the same time.


1. The main thread waits for new client connections using the accept() function.

2. When a new client connects, it calls pthread_create() to create a new, dedicated thread (client_chat) just for that client.

3. This dedicated thread waits for messages from its client using the recv() function.

4. The main thread immediately loops back to accept() to wait for the next client.

In effect, the "connection handling" thread (main) and the "per-client message receiving" threads all run independently and concurrently.

When a thread receives a message, it calls the send_msg function, which iterates through the clientList to broadcast the message to all other clients.

💻 **Client: Separation of Sending and Receiving Threads The client has its own major**
challenge: it must be able to receive messages from others in real-time, even while the user is typing their own message.

If it were single-threaded, the program would block on fgets() (waiting for user input), making it impossible to call recv() and receive incoming messages.

To solve this problem, the client program is also split into two threads:

1. Main Thread (main function): This thread is dedicated only to the "sending" role. It waits for the user's keyboard input (fgets) and sends (send) the message to the server.

2. Receiving Thread (receive function): Created with pthread_create(), this thread is dedicated only to the "receiving" role. It blocks on recv(), waiting for messages to arrive from the server.

By splitting the roles this way, the receive thread can display incoming messages from the server in real-time, even while the user is busy typing a new message in the main thread.

You can check out the code via the link(s) attached above!
<!--more-->
