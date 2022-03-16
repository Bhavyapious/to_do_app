# to_do_app
to do app in python
import tkinter
import tkinter.messagebox
import pickle

root=tkinter.Tk()
root.title("To do list App")
root.geometry("350x350")

def add_task():
    task=Entry_task.get()
    if task!="":

         Listbox_task.insert(tkinter.END,task)
         Entry_task.delete(0,tkinter.END)
    else:
        tkinter.messagebox.showwarning(title="Warning",message="You must enter the task")

def delete_task():
    try:
       task_index=Listbox_task.curselection()[0]
       Listbox_task.delete(task_index)
    except:
        tkinter.messagebox.showwarning(title="Warning", message="You must select a task")

# def load_task():
#     try:
#
#         tasks=pickle.load(open("tasks.date"," rb"))
#         Listbox_task.delete((0,tkinter.END))
#         for task in tasks:
#               Listbox_task.insert((tkinter.END,task))
#
#     except:
#         tkinter.messagebox.showwarning(title="Warning", message="Can not find tasks.dat")


# def save_task():
#     tasks=Listbox_task.get(0,Listbox_task.size())
#     pickle.dump(tasks,open("tasks.dat","wb"))

Frame_task=tkinter.Frame(root)
Frame_task.pack()

Listbox_task=tkinter.Listbox(Frame_task,height=3,width=50)
Listbox_task.pack(side=tkinter.LEFT)

Scroll_bar=tkinter.Scrollbar(Frame_task)
Scroll_bar.pack(side=tkinter.RIGHT,fill=tkinter.Y)

Scroll_bar.config(command=Listbox_task.yview)
Listbox_task.config(yscrollcommand=Scroll_bar.set)

Entry_task=tkinter.Entry(root,width=50)
Entry_task.pack()

button_add_task=tkinter.Button(root,text="Add tasks",width=40,command=add_task)
button_add_task.pack()

button_delete_task=tkinter.Button(root,text="Delete tasks",width=40,command=delete_task)
button_delete_task.pack()

# button_save_task=tkinter.Button(root,text="Save tasks",width=40,command=save_task)
# button_save_task.pack()
#
# button_load_task=tkinter.Button(root,text="Load tasks",width=40,command=load_task)
# button_load_task.pack()



root.mainloop()
