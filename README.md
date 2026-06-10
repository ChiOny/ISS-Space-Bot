# Space Bot: ISS Tracker and Webex Messenger

## Overview

Space Bot is a Python bot that tracks the International Space Station (ISS) in real time and shares its location inside a Webex chat room.

The project connects three APIs:

* ISS Location API
* OpenWeather Geocoding API
* Webex Messaging API

It collects the ISS latitude and longitude, converts the coordinates into a readable location, and posts the result automatically into a Webex room.

## Video Demonstration

[Watch the Space Bot demo video on OneDrive](https://herts365-my.sharepoint.com/:v:/g/personal/co24abm_herts_ac_uk/ESKnb04GytpOnPQOCR3PMzQBDN-nNmed12QzMOdQCkDJsQ?e=ox0zSI)

## Project Objectives

The main aims of this project were to:

* Connect and use multiple APIs together
* Read messages from a Webex room
* Respond when a user types a command such as `/5`
* Wait the number of seconds entered by the user
* Retrieve the current ISS location
* Convert raw latitude and longitude into a readable place name
* Practise using Python, JSON data, API requests, and environment variables securely

## APIs Used

### ISS Location API

Provides the live latitude and longitude coordinates of the International Space Station.

Example endpoint:

```text
http://api.open-notify.org/iss-now.json
```

### OpenWeather Geocoding API

Converts latitude and longitude coordinates into a readable geographic location.

Example endpoint:

```text
https://api.openweathermap.org/geo/1.0/reverse?lat={lat}&lon={lon}&appid={API_KEY}
```

### Webex Messaging API

Allows the bot to send and receive messages from a Webex room.

Example endpoint:

```text
https://webexapis.com/v1/messages
```

## How It Works

1. The bot loads the Webex token and OpenWeather API key from a local `.env` file.
2. It connects to a Webex room called `ISS Bot Room`.
3. It checks for messages starting with `/` followed by a number, such as `/5`.
4. The bot waits for the number of seconds entered.
5. It requests the live ISS position from the ISS Location API.
6. It sends the coordinates to the OpenWeather Geocoding API.
7. It posts the result back into the Webex room.

The message includes:

* Date and time of the reading
* Latitude and longitude
* City, region, country, or ocean/unknown location message

## Key Python Components

This project uses:

* `requests` for API communication
* `time` for delayed responses
* `python-dotenv` for loading environment variables securely
* `json` for handling API responses
* `try/except` blocks for basic error handling

## Security Considerations

Private API tokens are stored in a local `.env` file and are not uploaded to GitHub.

The `.env` file is included in `.gitignore` to prevent sensitive credentials from being exposed.

Example `.env` structure:

```text
WEBEX_TOKEN=your_webex_token
OPENWEATHER_KEY=your_openweather_key
```

## How to Run

Clone the repository:

```bash
git clone https://github.com/ChiOny/WTLabs.git
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

Create a `.env` file in the project folder:

```text
WEBEX_TOKEN=your_webex_token
OPENWEATHER_KEY=your_openweather_key
```

Run the program:

```bash
python space_bot.py
```

In Webex, type a command such as:

```text
/5
```

The bot will reply after five seconds with the current ISS location.

## Example Output

```text
🛰️ On Sat Nov 01 18:35:46 2025 UTC, the ISS was over Namibe Province, Angola.
Coordinates: (-15.6527°, 12.2120°)
```

If the ISS is over the ocean, the bot may respond with:

```text
🌍 The ISS is currently flying over: Over an ocean or unknown location.
```

## What I Learned

This project helped me practise:

* Combining multiple APIs in one Python program
* Working with live data
* Using environment variables to protect API keys
* Sending automated messages through Webex
* Structuring a small Python project
* Using GitHub Desktop for version control
* Writing clearer technical documentation

## References

* Cisco Webex Developer Portal. Available at: https://developer.webex.com/
* OpenWeather Geocoding API. Available at: https://openweathermap.org/api/geocoding-api
* Python Requests Library. Available at: https://requests.readthedocs.io/
* Python dotenv Library. Available at: https://pypi.org/project/python-dotenv/
* University of Hertfordshire Module Unit Notes – Web Technologies Labs

