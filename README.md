# Upgraded-Calculator
An improved version of the simple command-line calculator built while learning Python.




import tkinter as tk


def press(symbol):
    screen.insert(tk.END, symbol)


def clear():
    screen.delete(0, tk.END)


def calculate():
    try:
        answer = eval(screen.get())
        screen.delete(0, tk.END)
        screen.insert(0, answer)
    except:
        screen.delete(0, tk.END)
        screen.insert(0, "Error")


window = tk.Tk()
window.title("Calculator")


# Display
screen = tk.Entry(
    window,
    font=("Arial", 24),
    justify="right"
)

screen.grid(
    row=0,
    column=0,
    columnspan=4,
    padx=10,
    pady=10
)


# Buttons
buttons = [
    "7", "8", "9", "/",
    "4", "5", "6", "*",
    "1", "2", "3", "-",
    "0", ".", "=", "+"
]


row = 1
column = 0


for symbol in buttons:

    if symbol == "=":
        button = tk.Button(
            window,
            text=symbol,
            font=("Arial", 18),
            width=4,
            height=2,
            command=calculate
        )

    else:
        button = tk.Button(
            window,
            text=symbol,
            font=("Arial", 18),
            width=4,
            height=2,
            command=lambda s=symbol: press(s)
        )

    button.grid(
        row=row,
        column=column,
        padx=3,
        pady=3
    )

    column += 1

    if column == 4:
        column = 0
        row += 1


# Clear button
clear_button = tk.Button(
    window,
    text="C",
    font=("Arial", 18),
    width=4,
    height=2,
    command=clear
)

clear_button.grid(
    row=row,
    column=0,
    padx=3,
    pady=3
)


window.mainloop()
