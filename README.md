# ToDoListManager--Java
A simple console-based To- Do List Manager built using Java. It allows users to add, view ,delete, search, and manage tasks efficiently.
import java.util.Scanner;

public class ToDoListManager {
    static String[] tasks = new String[50];
    static int taskCount = 0;
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        System.out.println("========================================");
        System.out.println("   Welcome to To-Do List Manager!");
        System.out.println("========================================\n");

        boolean running = true;

        while (running) {
            displayMenu();
            int choice = getUserChoice();

            switch (choice) {
                case 1:
                    addTask();
                    break;
                case 2:
                    viewTasks();
                    break;
                case 3:
                    deleteTask();
                    break;
                case 4:
                    searchTask();
                    break;
                case 5:
                    countTasks();
                    break;
                case 6:
                    clearAllTasks();
                    break;
                case 7:
                    running = false;
                    exitProgram();
                    break;
                default:
                    System.out.println("❌ Invalid choice! Please try again.\n");
            }
        }
    }

    static void displayMenu() {
        System.out.println("========================================");
        System.out.println("           MAIN MENU");
        System.out.println("========================================");
        System.out.println("1. Add a new task");
        System.out.println("2. View all tasks");
        System.out.println("3. Delete a task");
        System.out.println("4. Search for a task");
        System.out.println("5. Count total tasks");
        System.out.println("6. Clear all tasks");
        System.out.println("7. Exit");
        System.out.println("========================================");
    }

    static int getUserChoice() {
        System.out.print("Enter your choice (1-7): ");
        int choice = scanner.nextInt();
        scanner.nextLine();
        return choice;
    }

    static void addTask() {
        if (taskCount >= tasks.length) {
            System.out.println("❌ Task list is full! Cannot add more tasks.\n");
            return;
        }

        System.out.print("Enter task description: ");
        String task = scanner.nextLine();

        tasks[taskCount] = task;
        taskCount++;

        System.out.println("✅ Task added successfully!\n");
    }

    static void viewTasks() {
        if (taskCount == 0) {
            System.out.println("📋 No tasks available. Your to-do list is empty!\n");
            return;
        }

        System.out.println("\n========================================");
        System.out.println("           YOUR TO-DO LIST");
        System.out.println("========================================");

        for (int i = 0; i < taskCount; i++) {
            System.out.println((i + 1) + ". " + tasks[i]);
        }

        System.out.println("========================================\n");
    }

    static void deleteTask() {
        if (taskCount == 0) {
            System.out.println("❌ No tasks to delete!\n");
            return;
        }

        viewTasks();
        System.out.print("Enter task number to delete (1-" + taskCount + "): ");
        int taskNumber = scanner.nextInt();
        scanner.nextLine();

        if (taskNumber < 1 || taskNumber > taskCount) {
            System.out.println("❌ Invalid task number!\n");
            return;
        }

        for (int i = taskNumber - 1; i < taskCount - 1; i++) {
            tasks[i] = tasks[i + 1];
        }

        tasks[taskCount - 1] = null;
        taskCount--;

        System.out.println("✅ Task deleted successfully!\n");
    }

    static void searchTask() {
        if (taskCount == 0) {
            System.out.println("❌ No tasks available to search!\n");
            return;
        }

        System.out.print("Enter search keyword: ");
        String keyword = scanner.nextLine();

        boolean found = false;
        System.out.println("\n========================================");
        System.out.println("         SEARCH RESULTS");
        System.out.println("========================================");

        for (int i = 0; i < taskCount; i++) {
            if (tasks[i].toLowerCase().contains(keyword.toLowerCase())) {
                System.out.println((i + 1) + ". " + tasks[i]);
                found = true;
            }
        }

        if (!found) {
            System.out.println("❌ No tasks found with keyword: " + keyword);
        }

        System.out.println("========================================\n");
    }

    static void countTasks() {
        System.out.println("📊 Total tasks in your list: " + taskCount + "\n");
    }

    static void clearAllTasks() {
        if (taskCount == 0) {
            System.out.println("❌ No tasks to clear!\n");
            return;
        }

        System.out.print("Are you sure you want to delete all tasks? (yes/no): ");
        String confirmation = scanner.nextLine();

        if (confirmation.equalsIgnoreCase("yes")) {
            for (int i = 0; i < taskCount; i++) {
                tasks[i] = null;
            }
            taskCount = 0;
            System.out.println("✅ All tasks cleared successfully!\n");
        } else {
            System.out.println("❌ Clear operation cancelled.\n");
        }
    }

    static void exitProgram() {
        System.out.println("\n========================================");
        System.out.println("   Thank you for using To-Do List Manager!");
        System.out.println("           Goodbye! 👋");
        System.out.println("========================================");
        scanner.close();
    }
}

// # To-Do List Manager (Java)

## 📌 Project Description
This is a simple console-based To-Do List Manager application developed in Java. It helps users manage their daily tasks easily.

## 🚀 Features
- Add new tasks
- View all tasks
- Delete tasks
- Search tasks
- Count total tasks
- Clear all tasks

## 🛠️ Technologies Used
- Java
- Scanner Class (for input)

## ▶️ How to Run
1. Clone the repository
2. Open in any Java IDE (Eclipse / IntelliJ / VS Code)
3. Compile and run the program

## 📂 File Structure
- ToDoListManager.java

## 💡 Future Improvements
- GUI version using Java Swing
- Save tasks in file (File Handling)
- Use ArrayList instead of array

## 👨‍💻 Author
Deep Ball
