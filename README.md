# To-Do-List
A simple and beginner-friendly To-Do List application built using Python. This project helps you manage daily tasks by allowing you to add, view, update, complete, and delete tasks.
tasks = []

def show_menu():
    print("\n====== TO-DO LIST MENU ======")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Update Task")
    print("4. Mark Task as Completed")
    print("5. Delete Task")
    print("6. Exit")

def view_tasks():
    if not tasks:
        print(" No tasks available.")
    else:
        print("\n Your Tasks:")
        for i, task in enumerate(tasks, start=1):
            status =  if task["completed"] else
            print(f"{i}. {status} {task['title']}")

def add_task():
    title = input("Enter new task: ").strip()
    if title:
        tasks.append({"title": title, "completed": False})
        print(" Task added.")
    else:
        print(" Task cannot be empty.")

def update_task():
    view_tasks()
    if not tasks:
        return
    try:
        num = int(input("Enter task number to update: "))
        if 1 <= num <= len(tasks):
            new_title = input("Enter new task title: ").strip()
            if new_title:
                tasks[num - 1]["title"] = new_title
                print(" Task updated.")
            else:
                print(" Task title cannot be empty.")
        else:
            print(" Invalid task number.")
    except ValueError:
        print(" Please enter a valid number.")

def complete_task():
    view_tasks()
    if not tasks:
        return
    try:
        num = int(input("Enter task number to mark as completed: "))
        if 1 <= num <= len(tasks):
            tasks[num - 1]["completed"] = True
            print(" Task marked as completed.")
        else:
            print(" Invalid task number.")
    except ValueError:
        print(" Please enter a valid number.")

def delete_task():
    view_tasks()
    if not tasks:
        return
    try:
        num = int(input("Enter task number to delete: "))
        if 1 <= num <= len(tasks):
            removed = tasks.pop(num - 1)
            print(f" Deleted task: {removed['title']}")
        else:
            print(" Invalid task number.")
    except ValueError:
        print(" Please enter a valid number.")

def main():
    while True:
        show_menu()
        choice = input("Choose an option (1-6): ").strip()

        if choice == '1':
            view_tasks()
        elif choice == '2':
            add_task()
        elif choice == '3':
            update_task()
        elif choice == '4':
            complete_task()
        elif choice == '5':
            delete_task()
        elif choice == '6':
            print(" Exiting To-Do List. Goodbye!")
            break
        else:
            print(" Invalid choice. Please enter a number between 1 and 6.")

if __name__ == "__main__":
    main()
