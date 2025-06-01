# CHROME-EXTENSION-FOR-PRODUCTIVITY-MANAGEMENT

COMPANY  : CODTECH IT SOLUTIONS

NAME     : MOPARTHI MANASA

INTERN ID: CT08DM984

DOMAIN   : MERN STACK WEB DEVELOPMENT

DURATION : 8 WEEKS

MENTOR   : NEELA SANTHOSH

# Description

A powerful Chrome extension designed to help users track their online time, block distracting websites, and boost productivity. It leverages the MERN stack — MongoDB, Express, React, and Node.js — to deliver robust backend services including secure data storage, user management, and analytics processing. The extension seamlessly integrates with Chrome Extension APIs to monitor browsing activity in real-time, enabling precise time tracking and dynamic blocking of distractions directly within the browser. This combination of modern web technologies and browser capabilities creates a smooth, responsive experience that empowers users to take control of their digital habits and maximize focus.

# 🚀 Features

**🔍 Real-Time Tab Monitoring**

Automatically detects and logs time spent on each website.

Tracks each active tab switch and records time spent before the switch.

**🛑 Website Blocking**
Allows users to define a list of distracting websites (e.g., social media, streaming).

Prevents access to blocked sites during focused hours using chrome.webRequest.

**📊 Daily Reports**
Generates a detailed daily summary of time spent per website.

Displays aggregated data in an intuitive UI within the extension popup or a separate dashboard.

**🔄 Sync Across Devices**
Stores data securely using a MongoDB database.

Ensures user preferences and data are consistent across devices.

# 🧱 Tech Stack
**Frontend (Chrome Extension)**

JavaScript (Vanilla)

HTML5, CSS3

Chrome Extension APIs (tabs, idle, storage, alarms, webRequest)

**Backend (MERN Stack)**

MongoDB: For storing activity logs and user preferences

Express.js: RESTful API endpoints

Node.js: Server logic

Mongoose: ODM for MongoDB

# 📁 Project Structure

PRODUCTIVITY-TRACKER/

│

├── backend/

│   ├── models/

│   │   └── Track.js         # Mongoose model for tracking records

│   ├── server.js            # Express server setup

│   ├── .env                 # Environment variables (e.g., DB URI)

│   └── package.json         # Backend dependencies

│

├── extension/

│   ├── background.js        # Core logic for tab monitoring and blocking

│   ├── popup.html           # Extension popup UI

│   ├── popup.js             # Handles report display in popup

│   ├── manifest.json        # Chrome extension manifest (v3)

│   └── package.json         # (optional, if using a build step)

│

├── package-lock.json

└── README.md

# 📦 Installation

**1. Clone the Repository**

cd productivity-tracker

git clone https://github.com/moparthimanasa/CHROME-EXTENSION-FOR-PRODUCTIVITY-MANAGEMENT.git


**2. Setup the Backend Server**

cd backend

npm init

touch .env

In your .env file:

MONGO_URI=mongodb://localhost:27017/productivity

PORT=5000

**Then start the server:**

node server.js

Or use:

npm run dev   # if using nodemon

**3. Load the Chrome Extension**
   
Go to chrome://extensions/

Enable "Developer Mode"

Click "Load Unpacked"

Select the extension/ folder

Now the extension will run and interact with the backend API.

Click the extension icon → "View Report" opens React or localhost:5000/report

# ⚙️ How It Works
The Productivity Tracker Chrome Extension integrates the browser environment with a MERN stack backend to monitor, store, and analyze your web activity in real time. Here's how the system operates from extension events to database storage:

**🧠 Step-by-Step Breakdown**

**1. Extension Starts**
When the Chrome extension is installed and activated, it begins monitoring your browser tabs through background.js.

It uses the Chrome tabs.onActivated event to detect when you switch tabs.

**2. Tracking Time Spent**

When a tab switch is detected:

It notes the URL of the previously active tab.

Calculates the time difference from when the last tab became active.

Parses the domain using new URL(url).hostname to extract just chatgpt.com, flipkart.com, etc.

Sends this info to the backend using a POST request to:

POST http://localhost:5000/track

Content-Type: application/json


**3. Backend Handling (server.js)**

The Express server receives this request.

It uses a Mongoose model (Track.js) to insert the record into MongoDB with fields:

site: Domain name

time: Seconds spent

date: Timestamp of the record


**4. Data Stored in MongoDB**

Example document:


{

  "_id": "683bceb40369a71b1f0946c4",
  
  "site": "www.flipkart.com",
  
  "time": 27.267,
  
  "date": "2025-06-01T03:53:24.295Z"
  
}

**5. Displaying Data in Popup**

When the user opens the popup (via popup.html and popup.js):

It fetches data from an endpoint like /report.

Displays time spent per site in a list or graphical format.

Allows a quick view of productivity.

# 🧪 Example Use Case

You start your day browsing ChatGPT.

Switch to Flipkart for shopping, then go to Amazon.

The extension logs each visit duration.

You open the popup to see a chart of where your time went.

You’ve blocked instagram.com, so it gets auto-blocked during work hours.

# 🚀 Future Enhancements

The Productivity Tracker is off to a great start, tracking website usage and browsing habits. Here’s how we can take it further:

**1.User Authentication**
Add secure login (JWT/OAuth) for personalized tracking and cross-device sync.

**2.Cloud Sync**
Sync data across multiple devices to maintain unified productivity profiles.

**3.Weekly/Monthly Reports**
Generate detailed reports with trend graphs for better insights.

**4.Interactive Dashboard**
Build a React dashboard for filtering, trend visualization, and quick insights.

**5.Custom Blocklist & Smart Blocking**
Allow user-defined blocklists and AI-driven distraction detection.

**6.Real-Time Notifications**
Warn users when usage limits on sites are exceeded.

**7.Focus Mode**
Temporarily block distractions for high-focus periods.

**8.AI Productivity Suggestions**
Offer AI-based tips for reducing distractions and optimizing work cycles.

# Output

**🔍 How to View Your Productivity Report**

To access your productivity insights:

Open a new browser tab.

Navigate to Extensions.

Click on the Productivity Management extension.

Select View Report.

![Image](https://github.com/user-attachments/assets/a556d70b-4052-4cdd-a765-a1f1249eb601)

As shown in the report below, the extension has tracked all the websites I’ve visited, giving a clear overview of how my time was spent online:

![Image](https://github.com/user-attachments/assets/f54d89f5-814f-4cbe-8183-4c533a10ca40)
