gps-tracking-server
Java and MongoDB based GPS object tracking server (TCP). This server can be used to handle TCP requests coming from GPS devices compatible with TK103 GPS data communication protocol.

Functionalities
Read incoming request and parse data stream.
Handle handshake signals and continues feedback requests.
Process location requests.
Find last known location within 30 seconds of time period and calculate distance between those two coordinates.
Insert processed coordinate to database.
Publish the coordinate to topic COO. ActiveMQ broker for live streaming, another service may subscribe to message topic /topic/COO. to retrieve data.
Publish message to REQSTATUS. topic (for analytics purposes).
Sends periodic reports about system status to given emails.
Sends periodic reports to given emails to notify recent offline devices.
(In order to make it work, ActiveMQ message publishing and email service must be enabled in system.yml)

Support
Supports for TK103 protocol.
Netty 4.0
MongoDB 3.6 as database.
ActiveMQ 5.14.5 as messaging server.
Installation
Maven clean and build project.
Copy gps folder to /opt directory.
Update system.yml file.
Run jar file named GpsServer2-2.0.0.
Additionally it is possible to use ubuntu upstart config file to run as background service, for that,
Rename GpsServer2-2.0.0-jar-with-dependencies.jar into GpsServer.jar.
Place this jar file on /opt directory.
Place gpsserver.conf file on /etc/init directiry, then start the service using service gpsserver start.
You can change this settings.
📍 GPS Tracking Server

A Java and MongoDB-based GPS tracking server that processes TCP requests from GPS devices compatible with the TK103 protocol.

🚀 Features

📡 Read and parse incoming GPS data streams

🔄 Handle handshake signals and continuous feedback requests

📍 Process real-time location data

⏱️ Track last known location within a 30-second interval

📏 Calculate distance between coordinates

💾 Store processed data in MongoDB

📢 Publish coordinates to messaging topics

📊 Send analytics and system status updates

📧 Email notifications for:

System status reports

Offline devices alerts

🧰 Tech Stack

☕ Java

🍃 MongoDB (v3.6)

⚡ Netty (v4.0)

📩 Apache ActiveMQ (v5.14.5)

📡 Messaging System

The server uses messaging queues for real-time communication:

Topic: COO
Publishes processed GPS coordinates for live tracking

Topic: REQSTATUS
Used for analytics and request status monitoring

➡️ External services can subscribe to:

/topic/COO

to receive live GPS updates.

⚙️ Installation & Setup
🔹 Step 1: Build Project
mvn clean install
🔹 Step 2: Setup Directory

Copy the gps folder to:

/opt
🔹 Step 3: Configuration

Update the configuration file:

system.yml

⚠️ Enable:

ActiveMQ messaging

Email service

🔹 Step 4: Run Server
java -jar GpsServer2-2.0.0.jar
🔄 Run as Background Service (Optional)
Steps:

Rename JAR file:

GpsServer2-2.0.0-jar-with-dependencies.jar → GpsServer.jar

Move file to:

/opt

Copy config file:

gpsserver.conf → /etc/init

Start service:

service gpsserver start
📌 Supported Protocol

✅ TK103 GPS Data Communication Protocol

📊 Functionality Overview

Accepts TCP connections from GPS devices

Parses incoming raw data

Processes and validates location information

Stores coordinates in database

Publishes data for real-time consumption

Generates reports and alerts

📬 Notifications

📧 Periodic system health reports

⚠️ Alerts for inactive/offline GPS devices

📌 Conclusion

This GPS tracking server provides a scalable and real-time solution for tracking GPS devices using TCP protocol, with support for messaging systems and monitoring capabilities.
