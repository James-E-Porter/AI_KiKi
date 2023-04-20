# AI Assistant Project

## 1. Introduction
Introduce the AI Assistant project, which aims to create an interactive and responsive assistant using Raspberry Pi, Arduino, Kinect camera, Pepper's Ghost displays, and AI models like ChatGPT. The assistant will have access to a camera for facial recognition and tracking, speech recognition, voice output, and control of various sensors and displays.

## 2. Hardware Setup
- **Raspberry Pi**: The Raspberry Pi 4 will act as the main server, handling incoming connections, controlling input from the user, and directing queries to the AI model. It will also interface with Arduino devices, sensors, and displays.
- **Arduino**: Two Arduino Uno boards will be used. One will control distance sensors and LED status lights, while the other will manage a small weather station. They will communicate with the Raspberry Pi through Wi-Fi.
- **Sensors and Displays**: The Kinect camera will provide facial recognition and tracking capabilities. The HC-SR04 ultrasonic sensor and PIR sensors will provide distance sensing and motion detection, respectively. The MAX7219 LED panel will be used as an LED status light. Two Pepper's Ghost displays will showcase 3D animated models based on user and AI input.

## 3. Weather Station
- **Components**: Arduino Uno, ESP8266 Wi-Fi module, BME280 sensor (temperature, humidity, and pressure), anemometer (wind speed), and solar radiation sensor.
- **Functionality**: The weather station will provide weather data, including temperature, humidity, pressure, wind speed, and solar radiation.
- **API Calls**: The weather station will expose endpoints for each type of data, allowing the Raspberry Pi to make requests and receive the information.

## 4. Software Implementation
- **Raspberry Pi**: Implement a Python script to create a server socket for incoming connections, handle data from Arduino devices, and communicate with the AI model.
- **AI Model**: Integrate ChatGPT checkpoints (or other suitable AI models) to process user requests and return appropriate responses. Utilize the provided Python code example to run the AI model on a separate thread.
- **Animations and Voice Output**: Select appropriate animations for AI responses and play them on the Pepper's Ghost display. Use a voice synthesizer library (e.g., pyttsx3) to convert text responses to speech and output them through a speaker.
- **Database of Known People**: Implement a SQLite database to store and retrieve information about people the AI assistant has met through conversations.

## 5. Multi-Threading
Utilize the provided Python code example that demonstrates how to run the AI model on a separate thread using the `threading` library. This ensures that the main server function can continue handling incoming connections and data without being blocked by AI model processing.

## 6. Networking
- **Local Network**: Set up a local Wi-Fi network using a separate router or create an ad-hoc network to enable communication between Raspberry Pi, Arduino devices, and the Android phone.
- **Socket Communication**: Implement socket communication in the Python script to send and receive data between devices on the local network.

## 7. Android Phone Integration
- **Unity App**: Create a Unity app that displays an idle animation with updates when the main software sends messages via Wi-Fi. The app will run on an Android phone and provide a secondary Pepper's Ghost display.
- **Communication**: Implement a client-server communication using sockets between the Raspberry Pi and the Android phone running the Unity app.

## 8. Conclusion
Summarize the features and capabilities of the AI Assistant project, and provide guidance on how users can customize or extend the project further to fit their needs.
