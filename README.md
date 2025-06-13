# calculator
import tkinter as tk
from tkinter import font

def click(btn):
    current = display_var.get()
    if btn == 'C':
        display_var.set("")
    elif btn == '=':
        try:
            result = eval(current)
            display_var.set(result)
        except Exception:
            display_var.set("Error")
    else:
        display_var.set(current + btn)

# Create main window
root = tk.Tk()
root.title("Professional Calculator")
root.geometry("350x500")
root.configure(bg="#2d2d2d")

# Set display
display_var = tk.StringVar()
display = tk.Entry(root, textvariable=display_var, font=("Helvetica", 28), bd=0, bg="#1e1e1e", fg="white", justify="right")
display.pack(fill="both", ipadx=8, ipady=30, padx=10, pady=20)

# Button layout
buttons = [
    ['7', '8', '9', '/'],
    ['4', '5', '6', '*'],
    ['1', '2', '3', '-'],
    ['C', '0', '=', '+']
]

btn_frame = tk.Frame(root, bg="#2d2d2d")
btn_frame.pack(expand=True, fill="both")

btn_font = font.Font(family="Helvetica", size=18, weight="bold")

for row in buttons:
    row_frame = tk.Frame(btn_frame, bg="#2d2d2d")
    row_frame.pack(expand=True, fill="both")
    for char in row:
        btn = tk.Button(row_frame, text=char, font=btn_font, bg="#3e3e3e", fg="white", bd=0,
                        activebackground="#5c5c5c", activeforeground="white",
                        command=lambda ch=char: click(ch))
        btn.pack(side="left", expand=True, fill="both", padx=5, pady=5)

root.mainloop()
