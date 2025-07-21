# To-Do-List
A simple and beginner-friendly To-Do List application built using Python. This project helps you manage daily tasks by allowing you to add, view, update, complete, and delete tasks.
tasks = []

def show_menu():
    print("\n===== TO-DO LIST MENU =====")
    print("1. Show Tasks")
    print("2. Add Task")
    print("3. Mark Task as Done")
    print("4. Exit")

def show_tasks():
    if not tasks:
        print("📭 No tasks available.")
    else:
        print("\n📝 Your Tasks:")
        for i, task in enumerate(tasks):
            status = "✅" if task["done"] else "❌"
            print(f"{i + 1}. {status} {task['title']}")

def add_task():
    title = input("Enter task: ").strip()
    if title:
        tasks.append({"title": title, "done": False})
        print("✅ Task added!")
    else:
        print("⚠️ Task cannot be empty.")

def mark_done():
    show_tasks()
    if not tasks:
        return
    try:
        task_num = int(input("Enter task number to mark as done: "))
        if 1 <= task_num <= len(tasks):
            tasks[task_num - 1]["done"] = True
            print("✅ Task marked as done.")
        else:
            print("❌ Invalid task number.")
    except ValueError:
        print("⚠️ Please enter a valid number.")

def main():
    while True:
        show_menu()
        choice = input("Choose an option (1-4): ").strip()

        if choice == '1':
            show_tasks()
        elif choice == '2':
            add_task()
        elif choice == '3':
            mark_done()
        elif choice == '4':
            print("👋 Goodbye! See you later.")
            break
        else:
            print("⚠️ Invalid choice. Please select 1 to 4.")

if __name__ == "__main__":
    main()

