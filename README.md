#include <iostream>
#include <cstdlib>   // For rand() and srand()
#include <ctime>     // For time()

int main() {
    char playAgain;

    do {
        // Seed the random number generator with the current time
        std::srand(static_cast<unsigned int>(std::time(0)));

        // Generate a random number between 1 and 100
        int secretNumber = std::rand() % 100 + 1;

        int userGuess;
        int attempts = 0;

        std::cout << "Welcome to the Number Guessing Game!" << std::endl;
        std::cout << "Try to guess the number between 1 and 100." << std::endl;

        do {
            std::cout << "Enter your guess: ";
            std::cin >> userGuess;

            attempts++;

            if (userGuess == secretNumber) {
                std::cout << "Congratulations! You guessed the correct number in " << attempts << " attempts." << std::endl;
            } else if (userGuess < secretNumber) {
                std::cout << "Too low! Try again." << std::endl;
            } else {
                std::cout << "Too high! Try again." << std::endl;
            }

        } while (userGuess != secretNumber);

        // Ask if the user wants to play again
        std::cout << "Do you want to play again? (y/n): ";
        std::cin >> playAgain;

    } while (playAgain == 'y' || playAgain == 'Y');

    return 0;
}
