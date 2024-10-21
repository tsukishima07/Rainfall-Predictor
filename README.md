# Rainfall-Predictor
It calculates the Rainfall with Humidity, Pressure and Temperature. It also displays the Actual Rainfall tooo

import tkinter as tk
from tkinter import messagebox

# Function to simulate a rainfall prediction based on input parameters
def predict_rainfall(temperature, pressure, humidity):
    return (0.1 * temperature) + (0.05 * pressure) + (0.2 * humidity)

# Function to be executed when the "Predict" button is pressed
def on_predict():
    try:
        # Get the values from the input fields
        temperature = float(entry_temperature.get())
        pressure = float(entry_pressure.get())
        humidity = float(entry_humidity.get())
        actual_rainfall = float(entry_actual_rainfall.get())

        # Predict rainfall
        predicted_rainfall = predict_rainfall(temperature, pressure, humidity)

        # Display the results
        result_text = f"Actual Rainfall: {actual_rainfall:.2f} mm\nPredicted Rainfall: {predicted_rainfall:.2f} mm"
        messagebox.showinfo("Rainfall Prediction Results", result_text)
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers for all fields.")

# Set up the main application window
root = tk.Tk()
root.title("Rainfall Prediction System")

# Create and place the labels and entry widgets
label_actual_rainfall = tk.Label(root, text="Actual Rainfall (in mm):")
label_actual_rainfall.grid(row=0, column=0, padx=10, pady=10)
entry_actual_rainfall = tk.Entry(root)
entry_actual_rainfall.grid(row=0, column=1, padx=10, pady=10)

label_temperature = tk.Label(root, text="Temperature (in °C):")
label_temperature.grid(row=1, column=0, padx=10, pady=10)
entry_temperature = tk.Entry(root)
entry_temperature.grid(row=1, column=1, padx=10, pady=10)

label_pressure = tk.Label(root, text="Pressure (in hPa):")
label_pressure.grid(row=2, column=0, padx=10, pady=10)
entry_pressure = tk.Entry(root)
entry_pressure.grid(row=2, column=1, padx=10, pady=10)

label_humidity = tk.Label(root, text="Humidity (in percentage):")
label_humidity.grid(row=3, column=0, padx=10, pady=10)
entry_humidity = tk.Entry(root)
entry_humidity.grid(row=3, column=1, padx=10, pady=10)

# Create and place the "Predict" button
button_predict = tk.Button(root, text="Predict Rainfall", command=on_predict)
button_predict.grid(row=4, columnspan=2, pady=20)

# Run the main event loop
root.mainloop()
