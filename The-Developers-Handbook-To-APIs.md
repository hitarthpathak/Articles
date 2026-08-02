# The Developer’s Handbook To APIs

![API](https://miro.medium.com/v2/resize:fit:720/format:webp/1*UsVZMECNZl0_Zpx9aqTWjA.avif)

An **API (Application Programming Interface)** is an invisible backbone of modern Software Development. It helps computers, software and systems to **communicate** and **share data** efficiently.

---

### TYPES OF APIs :-

**1. Web APIs -**

Web APIs allow communication between a Client (Browser) and a Server over the Internet using HTTP / HTTPS methods.

Example : Google Maps API, Twitter API, OpenWeather API, etc.

**2. Operating System APIs -**

Operating System APIs allow Desktop Applications to interact with the Operating System by allowing access to system resources like files, memory, etc.

Example : Windows API, Linux System Calls, macOS API, etc.

**3. Software Framework / Software Library APIs -**

Software Frameworks / Software Library APIs provide pre-defined functions and tools that developers can use in their Software.

Example : React API, Java API, Python Standard Library, etc.

**4. Hardware APIs -**

Hardware APIs enable Software to communicate directly with Hardware Components.

Example : Camera API, Bluetooth API, Printer Drivers, etc.

**5. Database APIs -**

Database APIs allow Software to interact with Databases for CRUD operations (Create, Read, Update, Delete).

Example : MongoDB API, PostgreSQL API, ODBC (Open Database Connectivity)

In this article, we will explore **Web APIs** in detail.

---

### WEB APIs :-

Web APIs are APIs specifically designed for web-based communication. They allow different Web Applications to exchange data over the Internet.

Web APIs can be divided into :

- Client-Side Web APIs (**Browser APIs**)
- Server-Side Web APIs (**Server APIs**)

---

**Browser APIs** — These are built-in browser APIs that allow developers to interact with the browser.

Types Of Browser APIs :

**1. DOM APIs —** Manipulate HTML & CSS

```
document.getElementById("result").innerText = "Success!";
document.getElementById("result").style.backgroundColor = "green";
```

**2. Fetch API —** Make HTTP Requests To Servers

```
fetch("/api/data")
  .then((res) => res.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Fetch Error : ", error));
```

*You can use the built-in **Fetch API** or external libraries like **Axios** or **React Query**.*

**3. Geolocation APIs —** Get User’s Location (With Permission)

```
navigator.geolocation.getCurrentPosition((position) => {
  let latitude = position.coords.latitude;
  let longitude = position.coords.longitude;
  console.log(`User's Latitude : ${latitude} \n User's Longitude : ${longitude}.`);
});
```

**4. Canvas / WebGL APIs —** Web Graphics & Animations

```
let canvas = document.getElementById("canvas");
let context = canvas.getContext("2d");
context.fillStyle = "blue";
context.fillRect(10, 10, 100, 50);
```

**5. Web Storage APIs —** Store or Retrieve Data From The Browser

```
let local_data = {
  name: "Hitarth Pathak",
  age: 24,
  single: true
};

// settings data
localStorage.setItem("data", JSON.stringify(local_data));

// getting data
let local_storage_data = JSON.parse(localStorage.getItem("data"));
console.log(local_storage_data);
```

***localStorage** and **sessionStorage** are Web Storage APIs, but **IndexedDB** and **Cookies** are not Web Storage APIs.*

*IndexedDB is a separate **Browser Storage API** and Cookies are part of **HTTP** based **State Management System**.*

**6. WebSocket APIs —** Real Time, Bi-Directional Communication

```
// Create A WebSocket Connection
let socket = new WebSocket("wss://example.com/socket");

// Connection Opened
socket.onopen = () => {
  console.log("WebSocket Connection Established");
  socket.send("Hello Server!");
};

// Listen For Messages
socket.onmessage = (event) => {
  console.log("Message From Server:", event.data);
};

// Handle Errors
socket.onerror = (error) => {
  console.error("WebSocket Error:", error);
};

// Connection Closed
socket.onclose = () => {
  console.log("WebSocket Connection Closed");
};
```

**7. Media APIs —** Accessing Device’s Hardware (Camera, Microphone, etc.)

```
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
  .then((stream) => console.log("Media stream:", stream))
  .catch((err) => console.error("Error accessing media devices:", err));
```

---

**Server API —** These are APIs built on Server that developers call on Front-End :

- To perform **CRUD** Operations (**C**reate, **R**ead, **U**pdate, **D**elete) on Database using **HTTP Methods** (POST, GET, PUT, DELETE)
- **User Authentication**
- **Server-Side Logic**

Server APIs usually have an endpoint through which developers can access the Data.

Types Of Server APIs :

**1. REST APIs —** (Representational State Transfer)
- Most common and industry standard (93% — [Postman Report 2025](https://voyager.postman.com/doc/postman-state-of-the-api-report-2025.pdf)).
- Uses HTTP methods on URL endpoints to access Resource (Data), mostly in JSON format.
- Stateless, i.e., each request is independent (server doesn’t store previous client sessions).

**2. GraphQL —** Query-Based API Architecture (Developed By Facebook)
- Clients specify exactly what data they need using a query language.
- Single endpoint for everything (no multiple URLs)
- Reduces over-fetching or under-fetching, client only gets what it wants (in JSON format).

**3. SOAP APIs —** (Simple Object Access Protocol)
- Uses XML-based protocol with strict standards.
- Very heavy with built-in security and transactions.
- Not much used in modern web dev, mainly used in legacy enterprise systems (banking, finance, etc.).

**4. gRPC APIs —** (Google Remote Procedure Call) (Developed By Google)
- High performance — generally faster than REST API & GraphQL API.
- Uses HTTP/2 and Protocol Buffers (Protobuf) to transfer binary data.
- Primarily used in microservices (server to server / internal communication).
- Not native in browsers — requires gRPC-Web proxy for front-end use.

```
| Type       | Format      | Endpoints | Key Strength          | Best For                     | Browser-Friendly? |
|------------|-------------|-----------|-----------------------|------------------------------|-------------------|
| REST       | JSON        | Multiple  | Simple & Widespread   | Public APIs, CRUD            | Yes               |
| GraphQL    | JSON        | Single    | Flexible Queries      | Complex Data                 | Yes               |
| SOAP       | XML         | Single    | Strict Security       | Enterprise / Legacy          | Yes               |
| gRPC       | Binary      | Services  | Speed & Efficiency    | Microservices / Internal     | No (Needs Proxy)  |
```

---

### API TESTING :-

API testing is the process of :

- Testing the functionality of the API to ensure it behaves as expected.
- Verifying that the API returns the correct response for different input values.
- Checking for error handling and validation of input.
- Testing for security vulnerabilities.
- Checking for performance and scalability of the API.

There are software used for API Testing such as — **Postman**, **SoapUI**, **Katalon Studio**, etc. You can also use VS Code extensions like **Thunder Client**, **REST Client**, **Postman VS Code**, etc.

---

### AUTHOR - HITARTH PATHAK