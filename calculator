#  A VERY SIMPLE CALCULATOR

# Estimated time
# 20-30 minutes
#
# Level of difficulty
# Easy
#
# Objectives
# Learn practical skills related to:
#
# using the Entry, Radiobutton and Button widgets,
# managing widgets with the grid manager,
# checking the validity of user input and handling errors.

# Scenario

# You need a calculator. A very simple and very specific calculator.
# it contains two fields that the user can use to enter arguments,
# a radio button to select the operation to perform, and a
# button initiating the evaluation:
#
# We expect the calculator to behave in the following way:
#
# if both fields contain valid (integer or float) numbers, clicking
# the Evaluate button should display an info window showing the
# evaluation's result;
# if any of the fields contains invalid data (e.g., a string, or
# a field is empty), clicking the Evaluate button should present
# an error window describing the problem, and the focus should be
# moved to the field causing the problem.
# Don't forget to protect your code from dividing by zero, and use
# the grid manager to compose the window interior.

import tkinter as tk

from tkinter import messagebox


def digits_only_1(*args):
    global last_number_1
    number = entry_1.get()
    if number == '' or number.isdigit():  # Field's content is valid.
        last_number_1 = number
    else:
        entry_1.set(last_number_1)
        field_1.focus_set()


def digits_only_2(*args):
    global last_number_2
    number = entry_2.get()
    if number == '' or number.isdigit():  # Field's content is valid.
        last_number_2 = number
    else:
        entry_2.set(last_number_2)


def display_result(*args):
    operation = options.get()
    num_1 = entry_1.get()
    num_2 = entry_2.get()

    if num_1 != 0 and num_2:
        if operation == 1:
            total = float(num_1) + float(num_2)  # PEP 484
            messagebox.showinfo("Result", total)
        elif operation == 2:
            total = float(num_1) - float(num_2)
            messagebox.showinfo("Result", total)
        elif operation == 3:
            total = float(num_1) * float(num_2)
            messagebox.showinfo("Result", total)
        elif operation == 4:
            if float(num_2) == 0:
                messagebox.showinfo("Error", message="Can not divide by zero")
                field_2.focus_set()
            else:
                total = float(num_1) / float(num_2)
                messagebox.showinfo("Result", total)
    else:
        messagebox.showerror('Error', 'Field empty')
        field_1.focus_set()


last_number_1 = 0
last_number_2 = 0

window = tk.Tk()

window.title("Simple Calculator", )

window.minsize(width=250, height=200)

entry_1 = tk.StringVar()
field_1 = tk.Entry(window, text="Field 1", textvariable=entry_1)
entry_1.trace('w', digits_only_1)
field_1.grid(row=0, column=0)

entry_2 = tk.StringVar()
field_2 = tk.Entry(window, text="Field 2", textvariable=entry_2)
entry_2.trace('w', digits_only_2)
field_2.grid(row=0, column=3)

options = tk.IntVar()
option_1 = tk.Radiobutton(window, text="+", variable=options, value=1)
# option_1.focus_set()  # it highlight just the text
option_1.focus_set()
option_1.grid(row=0, column=2)

option_2 = tk.Radiobutton(window, text="-", variable=options, value=2)
option_2.grid(row=1, column=2)

option_3 = tk.Radiobutton(window, text="*", variable=options, value=3)
option_3.grid(row=2, column=2)

option_4 = tk.Radiobutton(window, text="/", variable=options, value=4)
option_4.grid(row=3, column=2)

evaluate = tk.Button(window, text="Evaluate", command=display_result)
evaluate.grid(row=4, column=2)

window.mainloop()

# If the value can be neither an `int` of a `float`, PEP 484 suggest to use
# `float`.
