//Number game code in java
import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int playAgain = 1;  // Variable to track if the user wants to play another round
        
        // Loop for multiple rounds
        while (playAgain == 1) {
            int numberToGuess = random.nextInt(100) + 1; // generates a number between 1 and 100
            int attempts = 0;
            int maxAttempts = 10;  // Maximum attempts allowed
            boolean guessedCorrectly = false;

            System.out.println("Welcome to the Number Guessing Game!");
            System.out.println("I have generated a random number between 1 and 100.");
            System.out.println("You have " + maxAttempts + " attempts to guess it.");
            
            // Game loop for a single round
            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                // Check if the guess is too low, too high, or correct
                if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else if (userGuess > numberToGuess) {
                    System.out.println("Too high! Try again.");
                } else {
                    guessedCorrectly = true;
                    System.out.println("Congratulations! You guessed the correct number in " + attempts + " attempts.");
                }
            }

            // If the user didn't guess correctly, reveal the correct number
            if (!guessedCorrectly) {
                System.out.println("Sorry! You've used all " + maxAttempts + " attempts. The correct number was " + numberToGuess + ".");
            }

            // Ask if the user wants to play again
            System.out.print("Do you want to play another round? (1 for Yes, 0 for No): ");
            playAgain = scanner.nextInt();
        }

        // End of game
        System.out.println("Thanks for playing!");
        scanner.close();
    }
}
