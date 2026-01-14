![Logo](admin/solectrus-influxdb.png)
# ioBroker.solectrus-influxdb

[![NPM version](https://img.shields.io/npm/v/iobroker.solectrus-influxdb.svg)](https://www.npmjs.com/package/iobroker.solectrus-influxdb)
[![Downloads](https://img.shields.io/npm/dm/iobroker.solectrus-influxdb.svg)](https://www.npmjs.com/package/iobroker.solectrus-influxdb)
![Number of Installations](https://iobroker.live/badges/solectrus-influxdb-installed.svg)
![Current version in stable repository](https://iobroker.live/badges/solectrus-influxdb-stable.svg)

[![NPM](https://nodei.co/npm/iobroker.solectrus-influxdb.png?downloads=true)](https://nodei.co/npm/iobroker.solectrus-influxdb/)

**Tests:** ![Test and Release](https://github.com/patricknitsch/ioBroker.solectrus-influxdb/workflows/Test%20and%20Release/badge.svg)

🟢 ioBroker Solectrus-InfluxDB Adapter

Warning: This repository is experimental and unsupported; do not use it in production.

🚀 Overview

The Solectrus-InfluxDB adapter is designed to bridge ioBroker states—especially from Solar inverters and energy devices—to an InfluxDB time-series database with minimal configuration. It's based on the HA-Integration from Solectrus to push states to Influx for Solectrus Dashboard.

By continuously polling configured ioBroker states, caching the data, and writing timestamped measurements to InfluxDB, this adapter enables:

Powerful time-series analytics

Integration with Grafana or other visualization tools

Historical energy system monitoring

⚙️ Features

🎯 Multiple sensor support: Easily configure dozens of sensors with their data types and mappings

🔄 Dynamic state creation & extension: Automatically create ioBroker states or extend existing ones for sensor data

⏱️ Configurable polling interval (5-30 seconds) for flexible data write frequency

🔗 InfluxDB v2+ native support using official @influxdata/influxdb-client

✔️ Connection health monitoring via the info.connection state

🧹 Graceful shutdown with clean resource release and unsubscribe mechanisms

✨ User-defined sensors for custom measurements tailored to your needs

🛠️ Robust error handling and debug logging

🛠️ Configuration

Configure the adapter via the ioBroker admin UI with two main tabs:

InfluxDB Settings
🔑 Parameter	📝 Description
InfluxDB URL	URL of your InfluxDB instance
Organization	InfluxDB organization name
Bucket	Bucket name to write data into
Token	Secure API token for InfluxDB
Polling Interval	Interval (seconds) between writes (default 5, min 5, max 30)
Sensors Settings
🔧 Field	📖 Description
Enabled	Enable or disable individual sensors
Sensor Name	Human-readable name for the sensor
ioBroker Source State	ioBroker state ID to read data from
Datatype	Data type in InfluxDB (int, float, bool, string)
Influx Measurement	Measurement name in InfluxDB
Influx Field	Field name for the measurement
🧩 How It Works

Initialization
Validates InfluxDB configuration and establishes a connection with a test write.

Sensor Setup
Prepares sensor states in ioBroker (creates or updates) and subscribes to their source states.

State Changes
When subscribed source states update, the adapter caches new values and reflects changes in corresponding sensor states.

Data Writing
At configured intervals, cached sensor data is written as timestamped points into InfluxDB.

Monitoring
Adapter connection health is reflected in info.connection for easy monitoring.

🧑‍💻 Developer Notes

Language & Environment:
Written entirely in JavaScript using Node.js and the official InfluxDB v2 client
.

ioBroker Core:
Utilizes @iobroker/adapter-core for adapter lifecycle management and state handling.

State Management:
Creates or extends ioBroker states dynamically using setObject and extendObject.

Subscriptions:
Efficient subscription to source states ensures immediate cache updates on value changes.

Data Types:
Supports robust type mapping to handle integer, float, boolean, and string data seamlessly.

Error Handling:
Logs detailed error messages and updates info.connection accordingly for transparent operation.

Testing:
Connection tested with a minimal InfluxDB point on startup for early failure detection.

Extensibility:
Easily add new sensors by modifying the JSON config or the admin UI sensor table.

Shutdown Process:
Clears intervals, unsubscribes from states, and closes the InfluxDB client gracefully to avoid resource leaks.

📚 Resources

ioBroker Adapter Development Docs

InfluxDB JavaScript Client GitHub

InfluxDB v2 API Documentation

Grafana - Visualize InfluxDB Data

🛡️ License

This project is licensed under the MIT License – see the LICENSE
 file for details.

❤️ Contributing

Contributions are welcome! Please:

- Fork the repository

- Create a feature branch (git checkout -b feature/YourFeature)

- Commit your changes (git commit -m 'Add your feature')

- Push to the branch (git push origin feature/YourFeature)

- Open a Pull Request on GitHub

For major changes, please open an issue first to discuss what you would like to change.

Happy monitoring with Solectrus & InfluxDB! 📊⚡

## Changelog
<!--
	Placeholder for the next version (at the beginning of the line):
	### **WORK IN PROGRESS**
-->

### **WORK IN PROGRESS**
* (patricknitsch) initial release

## License
MIT License

Copyright (c) 2026 patricknitsch <patricknitsch@web.de>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.