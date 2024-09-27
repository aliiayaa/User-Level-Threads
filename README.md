# User-Level-Threads


class UserThread extends Thread {
    private String threadName;

    

    UserThread(String name) {
        this.threadName = name;
    }

    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(threadName + " is running - Count: " + i);
            try {
                // Simulating work with sleep
                Thread.sleep(500); // 500 ms
            } catch (InterruptedException e) {
                System.out.println(threadName + " was interrupted.");
            }
        }
        System.out.println(threadName + " has finished executing.");
    }
}

public class UserLevelThreadExample {
    public static void main(String[] args) {
        UserThread thread1 = new UserThread("User-Level Thread 1");
        UserThread thread2 = new UserThread("User-Level Thread 2");

        // Starting the threads
        thread1.start();
        thread2.start();

        // Wait for threads to finish
        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException e) {
            System.out.println("Main thread was interrupted.");
        }

        System.out.println("All user-level threads have completed.");
    }
}
