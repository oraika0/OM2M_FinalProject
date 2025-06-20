# Smart Indoor HVAC Control System (Based on oneM2M)

This project simulates an indoor smart HVAC (Heating, Ventilation, and Air Conditioning) control system. By integrating multiple heterogeneous devices (ACs, FANs, sensors) via a centralized oneM2M platform, users can manage all devices through a single user interface. The system automatically decides optimal device settings based on current environment data and user requests.

---

##  Motivation

In many indoor environments, air conditioners and fans are installed independently. Users must manually operate each unit, which is repetitive and error-prone (e.g., inconsistent temperature settings).  
This project aims to solve this issue by:

- Allowing users to send high-level abstract requests (e.g., target temperature, silent mode) via one interface
- Uploading requests and sensor data to the **OM2M in-cse**
- Using **Node-RED** (as AE) to subscribe, aggregate, and compute optimal device settings
- Devices **poll** OM2M to retrieve and apply the latest configuration

---
## Components (Simulated via App Inventor)

- User remote control
- Headcount sensor
- Thermometer
- Multiple AC units
- Multiple FAN units

---

## System Workflow

1. Start the OM2M in-cse server
2. Import and deploy the Node-RED flow
3. Create `smartRoom` AE and 5 
![AE](./snapshots/AE.png)
![container](./snapshots/container.png)

4. Subscribe to updates from `user`, `headcountSensor`, and `thermometer`
![subscription](./snapshots/subscription.png)
5. Launch 5 simulated App Inventor devices (User Remote, Sensors, ACs, FANs)
![AppInventor](./snapshots/AppInventor.png)
6. Simulate data posting (HTTP POST to corresponding containers)
![imagecotentInstance](./snapshots/contentInstance.png)

7. Node-RED computes settings and posts to `AC` / `FAN`
8. Each device polls its container (get la), retrieves the configuration, and deploys it




