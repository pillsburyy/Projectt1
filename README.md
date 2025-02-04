import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    static Scanner input = new Scanner(System.in);
    static ArrayList<String> taskk = new ArrayList<>();

    public static void main(String[] args) {
        while (true) {
            System.out.println("""
                     Please Choose an Option;
                     (1) Add a Task.
                     (2) Remove a Task.
                     (3) Update a Task.
                     (4) List all Tasks.
                     (0) Exit.
                    """);

            int userResponse = input.nextInt();
            input.nextLine(); 

            if (userResponse == 1) {
                add();
            } else if (userResponse == 2) {
                remove();
            } else if (userResponse == 3) {
                update();
            } else if (userResponse == 4) {
                listAll();
            } else if (userResponse == 0) {
                exit();
            } else {
                System.out.println("Invalid option, try again.");
            }
        }
    }

    static void add() {
        System.out.println("What task would you like to add:");
        String task = input.nextLine();
        taskk.add(task);
        System.out.println("Your task has been added.");
    }

    static void remove() {
        System.out.println("What task would you like to remove:");
        String task = input.nextLine();
        if (taskk.remove(task)) {
            System.out.println("Your task has been removed.");
        } else {
            System.out.println("Task not found.");
        }
    }


    static void update() {
        System.out.println("What task would you like to update:");
        String task = input.nextLine();

        if (taskk.contains(task)) {
            System.out.println("Give a description of the new update:");
            String taskUp = input.nextLine();
            taskk.set(taskk.indexOf(task), taskUp);
            System.out.println("Your task has been updated: " + taskUp);
        } else {
            System.out.println("Task not found.");
        }
    }

    static void listAll() {
        if (taskk.isEmpty()) {
            System.out.println("No tasks available.");
        } else {
            System.out.println("Tasks:");
            for (String t : taskk) {
                System.out.println(t);
            }
        }
    }

    static void exit() {
        System.out.println("Exiting the list...");
        System.exit(0);
    }
}
