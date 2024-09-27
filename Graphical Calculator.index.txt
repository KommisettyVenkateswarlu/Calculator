import tkinter as tk
def button_click(item):
    current_expression = entry_text.get()
    entry_text.set(current_expression + str(item))
def clear():
    entry_text.set("")
def evaluate():
    try:
        result = str(eval(entry_text.get()))
        entry_text.set(result)
    except:
        entry_text.set("Error")


root = tk.Tk()
root.title("Calculator")
root.geometry("400x500") 
entry_text = tk.StringVar()
entry = tk.Entry(root, textvariable=entry_text, font=('Arial', 20), bd=10, insertwidth=4, width=14, borderwidth=4, justify='right')
entry.grid(row=0, column=0, columnspan=4)
button_labels = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    'C', '0', '=', '+'
]
row_val = 1
col_val = 0

for label in button_labels:
    if label == "=":
        btn = tk.Button(root, text=label, padx=20, pady=20, font=('Arial', 18), command=evaluate)
    elif label == "C":
        btn = tk.Button(root, text=label, padx=20, pady=20, font=('Arial', 18), command=clear)
    else:
        btn = tk.Button(root, text=label, padx=20, pady=20, font=('Arial', 18), command=lambda l=label: button_click(l))

    btn.grid(row=row_val, column=col_val)

    col_val += 1
    if col_val > 3:
        col_val = 0
        row_val += 1
root.mainloop()
