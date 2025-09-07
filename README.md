# internorbit task1 in level numbergame
import java.util.Random;
import java.util.Scanner;

public class NumberGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int totalRounds = 0;
        int roundsWon = 0;
        boolean playAgain = true;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("Guess a number between 1 and 100.");

        while (playAgain) {
            totalRounds++;
            int numberToGuess = random.nextInt(100) + 1;
            int attemptsLeft = 7;
            boolean hasWon = false;

            System.out.println("\nRound " + totalRounds + " started!");
            System.out.println("You have " + attemptsLeft + " attempts.");

            while (attemptsLeft > 0) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attemptsLeft--;

                if (userGuess == numberToGuess) {
                    System.out.println("Congratulations! You guessed it right.");
                    hasWon = true;
                    roundsWon++;
                    break;
                } else if (userGuess > numberToGuess) {
                    System.out.println("Too high! Attempts left: " + attemptsLeft);
                } else {
                    System.out.println("Too low! Attempts left: " + attemptsLeft);
                }
            }

            if (!hasWon) {
                System.out.println("You are out of attempts. The number was: " + numberToGuess);
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("\nGame Over!");
        System.out.println("Total Rounds Played: " + totalRounds);
        System.out.println("Rounds Won: " + roundsWon);
        System.out.println("Thanks for playing!");

        scanner.close();
    }
