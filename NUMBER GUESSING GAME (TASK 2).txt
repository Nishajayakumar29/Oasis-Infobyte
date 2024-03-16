import java.util.Scanner;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int minRange = 1;
        int maxRange = 100;
        int attemptsLimit = 6; // Limiting the number of attempts
        int score = 0; // Initializing score
        
        System.out.println("Welcome to the Number Game!..........Let's Play......");
        
        boolean playAgain = true;
        while (playAgain) {
            int generatedNumber = random.nextInt(maxRange - minRange + 1) + minRange;
            System.out.println("I have generated a number between " + minRange + " and " + maxRange);
            
            int attempts = 0;
            while (attempts < attemptsLimit) {
                System.out.print("come on guess the number and enter : ");
                int userGuess = scanner.nextInt();
                attempts++;
                
                if (userGuess == generatedNumber) {
                    System.out.println("Wow!..........Congratulations! You've guessed the correct number!");
                    score++; // Incrementing score for each correct guess
                    break;
                } else if (userGuess < generatedNumber) {
                    System.out.println("oops!...Too low! Try again.");
                } else {
                    System.out.println("oops!..Too high! Try again.");
                }
            }
            
            if (attempts == attemptsLimit) {
                System.out.println("Sorry, you've reached the maximum number of attempts. The correct number was: " + generatedNumber);
            }
            
            System.out.println("Your score is : " + score);
            
            // Ask if the user wants to play again
            System.out.print("Do you wish to play again? (yes/no): ");
            String playAgainInput = scanner.next();
            playAgain = playAgainInput.equalsIgnoreCase("yes");
        }
        
        System.out.println("Thank you for playing!");
        scanner.close();
    }
}
