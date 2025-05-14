# Smart-Bin Project

## Project Overview

The Smart-Bin System is an IoT-based project designed to monitor garbage levels in dustbins placed in public areas (e.g., temples). It uses an Ultrasonic Sensor (HC-SR04) to detect garbage levels and sends data to an Arduino Uno, which transmits it to a connected computer. A Python script processes the data and displays it in real-time using a Flask web interface.

## Features

- Real-time monitoring of garbage levels in dustbins
- Displays garbage level percentage on a web interface
- Stores and shows the latest 20 entries with timestamps
- Automatic update of garbage levels every minute
- Simple and user-friendly web interface

## System Components

### Hardware

- Arduino Uno (Microcontroller)
- HC-SR04 Ultrasonic Sensor (Distance measurement)
- USB Cable (Arduino to Computer)
- Jumper Wires (Connections)

### Software

- Arduino IDE (For uploading code)
- Python 3 (For serial communication and data handling)
- Flask (Web framework)
- HTML/CSS/JavaScript (Frontend)
- JSON (Data storage format)

## Project Structure

```

Smart-Bin/
├── Arduino\_Code/
│   └── smart\_bin.ino             # Arduino code for measuring garbage levels
├── Server/
│   ├── app.py                    # Flask app for serving web interface
│   ├── read\_serial.py            # Python script to read serial data from Arduino
│   ├── requirements.txt          # Python dependencies
│   ├── data/
│   │   └── garbage\_data.json     # JSON file storing garbage level data
│   ├── templates/
│   │   └── index.html            # HTML template for web interface
│   └── static/
│       └── style.css             # CSS styling for web page
└── README.md                     # Project documentation

````

## How It Works

1. **Sensor Input**: The HC-SR04 sensor measures the distance to the garbage inside the bin.
2. **Arduino Processing**: The Arduino calculates the percentage fill level.
3. **Serial Communication**: Data is sent from Arduino to the computer via USB.
4. **Python Script**: Serial data is read and saved in a JSON file.
5. **Flask Web Server**: Data is displayed on a local web interface.

## Hardware Setup

### HC-SR04 Pin Connections

| HC-SR04 Pin | Arduino Pin    |
|-------------|----------------|
| VCC         | 5V             |
| GND         | GND            |
| Trig        | Digital Pin 9  |
| Echo        | Digital Pin 10 |

### Power Supply

Ensure the Arduino is powered through a USB connection to the computer.

## Software Setup

### 1. Arduino Code Upload

- Open `Arduino_Code/smart_bin.ino` using the Arduino IDE.
- Select the correct board and port.
- Upload the code to the Arduino Uno.

### 2. Python Environment Setup

Navigate to the server directory and install dependencies:

```bash
cd Smart-Bin/Server
pip install -r requirements.txt
````

### 3. Run Flask Web Server

Open two terminals.

* In the first terminal:

```bash
python read_serial.py
```

* In the second terminal:

```bash
python app.py
```

Open a web browser and go to:
`http://127.0.0.1:5000/`

## Usage

Once the setup is complete, the Arduino continuously measures the garbage level and transmits the data. The Python script stores this data, and the Flask server displays it on a web interface. The page refreshes automatically every minute.

## Web Interface

The interface displays the latest 20 garbage level readings along with their respective timestamps and percentage values.

## Future Enhancements

* Remote monitoring using cloud platforms
* Full bin alerts via SMS or Email
* Data analytics to predict future fill levels

## Troubleshooting

### Arduino Not Detected

* Verify correct board and port selection in Arduino IDE
* Check the USB cable connection

### Serial Data Not Displayed

* Ensure `read_serial.py` is running
* Verify and update the COM port in the script

### Web Interface Not Loading

* Confirm that `app.py` is running
* Open the correct URL: `http://127.0.0.1:5000/`

## Contributing

Contributions are welcome. You can fork the repository and submit pull requests.

Potential improvements include:

* Adding support for multiple bins
* Mobile application development
* Notification system integration

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.
