/* John Renzel M. Fangon 
/* CC2 1B

import java.util.Scanner;

public class PasswordValidationSystem {

    public static void main(String[] args) {
        
        // Create a Scanner object to take input
        Scanner scanner = new Scanner(System.in);

        // Loop to repeatedly ask for a valid password
        while (true) {
            System.out.print("Enter your password: ");
            String password = scanner.nextLine();

            // Check if the password meets the criteria
            if (isValidPassword(password)) {
                System.out.println("Your password is valid!");
                break;  // Exit the loop once a valid password is entered
            } else {
                System.out.println("Password must contain at least 8 characters, including one uppercase letter and one number.");
            }
        }

        // Close the scanner
        scanner.close();
    }

    // Method to validate the password
    public static boolean isValidPassword(String password) {
        // Check if the password length is at least 8 characters
        if (password.length() < 8) {
            return false;
        }

        // Check if the password contains at least one uppercase letter
        boolean containsUppercase = false;
        boolean containsNumber = false;

        for (char ch : password.toCharArray()) {
            if (Character.isUpperCase(ch)) {
                containsUppercase = true;
            } else if (Character.isDigit(ch)) {
                containsNumber = true;
            }

            // If both conditions are met, no need to check further
            if (containsUppercase && containsNumber) {
                return true;
            }
        }

        // Return false if any condition is not met
        return containsUppercase && containsNumber;
    }
}
