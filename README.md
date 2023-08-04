# JavaTask
Codsoft Java Internship Task Coding board 

import java.util.Random;
import java.util.Scanner;

public class NumberGame {
    public static void main(String[] args) {
        int min = 1;
        int max = 100;
        int maxAttempts = 10;
        int score = 0;

        Random random = new Random();

        Scanner scanner = new Scanner(System.in);

        boolean playAgain = true;

        while (playAgain) {
         
            int randomNumber = random.nextInt(max - min + 1) + min;
            int attempts = 0;
            boolean guessedCorrectly = false;

            while (!guessedCorrectly && attempts < maxAttempts) {
                
                System.out.print("Round " + (attempts + 1) + ": Enter your guess (between " + min + " and " + max + "): ");
                int userGuess = scanner.nextInt();

                attempts++;
                if (userGuess == randomNumber) {
                    System.out.println("Congratulations! Your guess is correct.");
                    guessedCorrectly = true;
                    score += maxAttempts - attempts + 1;
                } else if (userGuess < randomNumber) {
                    System.out.println("Too low. Try again!");
                } else {
                    System.out.println("Too high. Try again!");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Round " + attempts + ": Sorry, you ran out of attempts. The correct number was: " + randomNumber);
            }
            System.out.print("Do you want to play again? (y/n): ");
            String playAgainChoice = scanner.next();
            playAgain = playAgainChoice.equalsIgnoreCase("y");
        }
       
        System.out.println("Your final score: " + score);

        scanner.close();
    }
}
