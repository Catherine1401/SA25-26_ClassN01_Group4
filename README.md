# 📱 Mobile Messaging Application

**(Monolithic Architecture)**

---

## 1. Project Introduction

This project aims to develop a **mobile messaging application** that allows users to communicate with each other **in real time**.

The system is designed using a **Monolithic Architecture**, where all functionalities are implemented within **a single, unified application**.

The project is carried out as part of the **Software Architecture** course, with a focus on:

* Analyzing **architectural decisions**
* Evaluating **software quality attributes** of the system

---

## 2. Executive Summary

The messaging application enables users to:

* Connect to the system using a **unique username**
* Send and receive **text messages in real time**
* Communicate **concurrently with multiple users**

The system follows a **Client–Server architecture**, where the server is implemented as a **Monolithic application**.

All core processing logic is centralized in a single application, including:

* User connection management
* Message processing and distribution

This approach helps to:

* Simplify deployment
* Support rapid development in the early stages

---

## 3. Project Requirements & Goals

### 3.1 Functional Requirements

* Users can connect to the server using a **unique username**
* Users can **send and receive text messages**
* Messages are delivered **in real time**
* The system supports **multiple concurrent users**

### 3.2 Non-Functional Requirements

* **Low latency**: Messages are delivered almost instantly
* **Reliability**: The system operates stably under normal conditions
* **Ease of deployment**: Suitable for small development teams
* **Maintainability**: Simple and understandable system structure

### 3.3 Project Goals

* Apply **Monolithic Architecture** to a real-time system
* Evaluate the **advantages and limitations** of Monolithic Architecture
* Satisfy key **quality attributes** of a messaging application

---

## 4. Architectural Design & Implementation

### 4.1 Architectural Overview

The system is designed based on a **Client–Server Architecture**, consisting of:

#### Client (Mobile)

* Displays the user interface
* Sends and receives messages

#### Monolithic Server

* Manages user connections
* Handles business logic
* Distributes messages in real time

*(Optional)*: Data storage

→ All server-side components are deployed within **a single application**.

---

### 4.2 Monolithic Architecture Diagram

```
+--------------------------------------------------------------+
|                        Mobile Client                         |
|                       Flutter (Android)                      |
|--------------------------------------------------------------|
| - UI / UX                                                    |
| - Message Input & Display                                    |
| - WebSocket Client                                           |
+--------------------------------------------------------------+
                            |
                            |  WebSocket (Real-time)
                            v
+================================================================+
|                     BACKEND APPLICATION                        |
|               Monolithic Chat Server (Single Deploy)           |
|================================================================|
|                                                                |
|  +------------------+                                          |
|  |  Connection      |<------------------------------+          |
|  |  Controller      |   Internal Control Flow       |          |
|  |  (WebSocket API) |-------------------------------+          |
|  +------------------+                               |          |
|           |                                         |          |
|           v                                         |          |
|  +------------------+                               |          |
|  |  Business Logic  |                               |          |
|  |  Layer           |                               |          |
|  |  - Message Logic |                               |          |
|  |  - User Session  |                               |          |
|  |  - Realtime Event|                               |          |
|  +------------------+                               |          |
|           |                                         |          |
|           v                                         |          |
|  +------------------+                               |          |
|  | Data Access Layer|                               |          |
|  | (Repository)     |                               |          |
|  +------------------+                               |          |
|           |                                         |          |
|           +-------------------- Control Link -------+          |
|                                                                |
+================================================================+
                            |
                            v
+--------------------------------------------------------------+
|                   Data Storage Layer                         |
|--------------------------------------------------------------|
| - PostgreSQL (Supabase): Users, Messages, Groups             |
| - Redis (Optional)    : Sessions, Online Status              |
+--------------------------------------------------------------+
```

#### Architecture Explanation

* The client communicates **directly** with the server
* The server handles **all functionalities** within a single unified system
* Real-time communication is achieved using **WebSocket**

---

### 4.3 Technologies Used

| Component     | Technology             |
| ------------- | ---------------------- |
| Client        | Android / Flutter      |
| Server        | Monolithic Application |
| Communication | WebSocket              |
| Storage       | Database               |

---

### 4.4 Rationale for Choosing Monolithic Architecture

The **Monolithic Architecture** was chosen because:

* It is suitable for **small to medium-sized projects**
* It is **easy to develop and deploy**
* It reduces **architectural complexity**
* It supports **learning objectives and architectural analysis**

---

## 5. Testing & Verification

### 5.1 Testing Strategy

* **Unit Testing**: Verify message-processing functions
* **Integration Testing**: Validate client–server communication
* **Performance Testing**: Measure latency under concurrent messaging load

### 5.2 Results

* Messages are delivered **almost instantly**
* The system remains **stable with multiple concurrent connections**
* The Monolithic Architecture **meets the current project requirements**

---

## 6. Conclusion & Reflection

The project successfully delivered a **real-time mobile messaging application** based on a **Monolithic Architecture**.

This architecture is well-suited to:

* The educational objectives of the course
* The current scale of the project

It also helps demonstrate the relationship between **architectural decisions** and **software quality attributes**.

### Future Enhancements

* Modularize components as the system scales
* Migrate to **Microservices Architecture** for large user bases
* Add **multimedia messaging** support
