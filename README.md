# calculator
import tkinter as tk
from tkinter import messagebox

# Function to perform calculation
def calculate(op):
    try:
        num1 = float(entry1.get())
        num2 = float(entry2.get())

        if op == '+':
            result = num1 + num2
        elif op == '-':
            result = num1 - num2
        elif op == '*':
            result = num1 * num2
        elif op == '/':
            if num2 == 0:
                result_label.config(text="❌ Cannot divide by zero!")
                return
            result = num1 / num2
        result_label.config(text=f"Result: {result}")
    except ValueError:
        result_label.config(text="⚠️ Enter valid numbers!")

# Create window
root = tk.Tk()
root.title("Simple Calculator")
root.geometry("300x300")
root.resizable(False, False)

# Heading
tk.Label(root, text="Simple Calculator", font=("Arial", 16)).pack(pady=10)

# Input fields
entry1 = tk.Entry(root, width=15, font=("Arial", 12))
entry1.pack(pady=5)
entry2 = tk.Entry(root, width=15, font=("Arial", 12))
entry2.pack(pady=5)

# Buttons
btn_frame = tk.Frame(root)
btn_frame.pack(pady=10)

tk.Button(btn_frame, text="+", width=5, command=lambda: calculate('+')).grid(row=0, column=0, padx=5, pady=5)
tk.Button(btn_frame, text="-", width=5, command=lambda: calculate('-')).grid(row=0, column=1, padx=5, pady=5)
tk.Button(btn_frame, text="×", width=5, command=lambda: calculate('*')).grid(row=1, column=0, padx=5, pady=5)
tk.Button(btn_frame, text="÷", width=5, command=lambda: calculate('/')).grid(row=1, column=1, padx=5, pady=5)

# Result display
result_label = tk.Label(root, text="Result:", font=("Arial", 14), fg="blue")
result_label.pack(pady=15)

# Start GUI loop
root.mainloop()
