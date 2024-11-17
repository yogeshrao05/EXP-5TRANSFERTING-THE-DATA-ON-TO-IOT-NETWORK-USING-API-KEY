# EXPERIMENT-05-TRANSFERRING-DATA-TO-IOT-NETWORK-USING-API-KEY

### NAME: YOGESH RAO S D
### REGISTER NUMBER:212222110055
### DEPARTMENT:BE CSE(IOT)
### YEAR: III

## Aim:
To transfer sensor data to an IoT platform (ThingSpeak) using an API key.

## Apparatus Required:
ThingSpeak Channel ID and Write API Key: A valid ThingSpeak account and API key.
Microcontroller (e.g., ESP32/ESP8266, NodeMCU, etc.): For collecting sensor data and transmitting it to ThingSpeak.
Sensor Modules (e.g., Temperature, Humidity, etc.): For data collection.
Computer System: For writing and uploading the code to the microcontroller.
Internet Connection: To send the data to the ThingSpeak platform.
Theory:
IoT networks enable the exchange of data between devices through the internet. ThingSpeak is an IoT analytics platform that allows users to collect, store, and visualize sensor data using API keys. In this experiment, we use the ThingSpeak API to send sensor data periodically, allowing remote monitoring and analysis.

## Procedure:
Setup ThingSpeak Channel:</br>

Create a ThingSpeak account and generate a channel with the required fields (e.g., temperature, humidity).
Obtain the Write API Key for your channel, which is used for sending data.

Setup the Microcontroller and Sensors:</br>

Connect the required sensors (e.g., temperature sensor, humidity sensor) to the microcontroller.
Ensure the microcontroller is connected to the internet (using Wi-Fi or Ethernet).

Code for Sending Data:</br>

Write a Python script (or Arduino code, depending on the platform) to read data from sensors.
Construct the URL to send data to ThingSpeak using the API key and channel ID.
Use the requests library to send HTTP POST requests containing sensor data to ThingSpeak.
Code Implementation: Here’s the Python code that reads sensor data and sends it to ThingSpeak:

## python
```
import requests
import time
channel_id = "2746398"
write_api_key = "ZU0LOM1J0IRXI17A" 
url = f"https://api.thingspeak.com/update?api_key={write_api_key}"
field_1 = 23.5 
field_2 = 65    
payload = {
    'field1': field_1,
    'field2': field_2
}
def send_to_thingspeak(payload):
    try:
        response = requests.post(url, params=payload)
        if response.status_code == 200:
            print(f"Data sent successfully: {payload}")
        else:
            print(f"Failed to send data. Status Code: {response.status_code}")
    except Exception as e:
        print(f"Error: {e}")
while True:
    send_to_thingspeak(payload)
    time.sleep(15)
``` 

## Outputs:
![image](https://github.com/user-attachments/assets/b36faf15-a139-48e6-b8b6-c58e629a952c)
![WhatsApp Image 2024-11-15 at 08 42 00_6c42b3b4](https://github.com/user-attachments/assets/d5b3285f-066b-4528-9542-41fbe5f0fa23)

## Simulation Screenshots:
![WhatsApp Image 2024-11-15 at 08 43 00_66e01b30](https://github.com/user-attachments/assets/cd216c01-7ed5-4bab-a47a-5c162f247a19)
![image](https://github.com/user-attachments/assets/4c68de73-5635-4869-a381-1fa16372fbef)

## Results:
The sensor data was successfully transferred to the ThingSpeak IoT platform using an API key. The experiment demonstrated how to send data from sensors to an IoT network and visualize it remotely using ThingSpeak. The periodic data updates were successfully logged and displayed on the ThingSpeak platform.
