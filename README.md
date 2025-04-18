import tkinter as tk

def add_task():
    task = task_entry.get()
    if task != "":
        task_list.insert(tk.END, task)
        task_entry.delete(0, tk.END)  # Clear the entry box

def remove_task():
    try:
        selected_task_index = task_list.curselection()[0]
        task_list.delete(selected_task_index)
    except IndexError:
        pass

# Create the main window
root = tk.Tk()
root.title("To-Do List")
root.geometry("400x400")

# Create the main frame
frame = tk.Frame(root)
frame.pack(pady=10)
# Create a Listbox to hold the tasks
task_list = tk.Listbox(frame, width=50, height=10, bd=0, selectmode=tk.SINGLE)
task_list.pack(side=tk.LEFT)

# Create a scrollbar
scrollbar = tk.Scrollbar(frame)
scrollbar.pack(side=tk.RIGHT, fill=tk.Y)

# Link the scrollbar to the Listbox
task_list.config(yscrollcommand=scrollbar.set)
scrollbar.config(command=task_list.yview)

# Create an entry box to add tasks
task_entry = tk.Entry(root, width=52)
task_entry.pack(pady=10)

# Create buttons
add_button = tk.Button(root, text="Add Task", width=48, command=add_task)
add_button.pack(pady=10)

remove_button = tk.Button(root, text="Remove Task", width=48, command=remove_task)
remove_button.pack(pady=5)

# Run the application
root.mainloop()
