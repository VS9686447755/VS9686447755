 import requests

API_KEY = "your_api_key_here"  # Replace this with your actual API key
BASE_URL = "http://api.weatherapi.com/v1/history.json"


def get_weather(date):
    url = f"{BASE_URL}?key={API_KEY}&q=London&dt={date}"
    response = requests.get(url)
    data = response.json()
    temp_c = data["forecast"]["forecastday"][0]["day"]["maxtemp_c"]
    print(f"Temperature on {date}: {temp_c}°C")


def get_wind_speed(date):
    url = f"{BASE_URL}?key={API_KEY}&q=London&dt={date}"
    response = requests.get(url)
    data = response.json()
    wind_speed = data["forecast"]["forecastday"][0]["day"]["maxwind_kph"]
    print(f"Wind Speed on {date}: {wind_speed} kph")


def get_pressure(date):
    url = f"{BASE_URL}?key={API_KEY}&q=London&dt={date}"
    response = requests.get(url)
    data = response.json()
    pressure_mb = data["forecast"]["forecastday"][0]["day"]["maxpressure_mb"]
    print(f"Pressure on {date}: {pressure_mb} mb")


def main():
    while True:
        print("Options:")
        print("1. Get weather")
        print("2. Get Wind Speed")
        print("3. Get Pressure")
        print("0. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            date = input("Enter the date (YYYY-MM-DD): ")
            get_weather(date)

        elif choice == "2":
            date = input("Enter the date (YYYY-MM-DD): ")
            get_wind_speed(date)

        elif choice == "3":
            date = input("Enter the date (YYYY-MM-DD): ")
            get_pressure(date)

        elif choice == "0":
            print("Exiting the program.")
            break

        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
