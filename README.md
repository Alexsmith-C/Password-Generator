import tkinter as tk
from tkinter import messagebox
import random
import string

def generate_password():
    try:
        length = int(length_entry.get())
        if length < 4:
            messagebox.showerror("Error", "Password length must be at least 4")
            return
        chars = string.ascii_letters + string.digits + string.punctuation
        password = ''.join(random.choice(chars) for _ in range(length))
        password_entry.delete(0, tk.END)
        password_entry.insert(0, password)
    except ValueError:
        messagebox.showerror("Error", "Please enter a valid number")
        if length_entry.get() >= "26":
            messagebox.showerror("Error", "Please enter a length for the password")

def clear_password():
    password_entry.delete(0, tk.END)

root = tk.Tk()
root.title("Password Generator")
root.geometry("800x500")
root.configure(bg="Black")

heading = tk.Label(root, text="Password Generator", font=('Arial', 30, 'bold'), fg="Green", bg='Black')
heading.pack(pady=20)

heading = tk.Label(root, text="By Muhammad Musa Bilal", font=('Arial', 15, 'bold'), fg="Gray", bg='Black')
heading.pack(pady=20)

length_frame = tk.Frame(root, bg="black")
length_frame.pack(pady=10)

length_label = tk.Label(length_frame, text="Enter length:", font=('Arial', 20, 'bold'), fg="White", bg='Black')
length_label.pack(side=tk.LEFT, padx=5)

length_entry = tk.Entry(length_frame, font=('Arial', 15, 'bold'), width=5)
length_entry.pack(side=tk.LEFT)

password_entry = tk.Entry(root, font=('Arial', 40, 'bold'), bg='Dark Gray', justify='center')
password_entry.pack(pady=20)

btn_frame = tk.Frame(root, bg='Black')
btn_frame.pack(pady=10)

generate_btn = tk.Button(btn_frame, text="Generate", font=("Fira Code", 15, "bold"), bg="#00FFAA", fg="Black",command=generate_password)

generate_btn.pack(side=tk.LEFT, padx=10)

clear_btn = tk.Button(btn_frame, text="Clear", font=("Titan One", 20, "bold"), bg="#FF8888", fg="Black",command=clear_password)

clear_btn.pack(side=tk.LEFT, padx=10)

root.mainloop()
