#include <iostream>
#include <ctime>
#include <cstdlib>

using namespace std;

// Function to get user's choice
char getUserChoice() {
    char choice;
    cout << "Enter your choice (r for rock/p for paper/s for scissors): ";
    cin >> choice;
    return choice;
}

// Function to get computer's choice
char getComputerChoice() {
    char choices[] = {'r', 'p', 's'};
    int index = rand() % 3;
    return choices[index];
}

// Function to determine the winner
string determineWinner(char userChoice, char computerChoice) {
    if (userChoice == computerChoice) {
        return "It's a tie!";
    } else if ((userChoice == 'r' && computerChoice == 's') ||
               (userChoice == 'p' && computerChoice == 'r') ||
               (userChoice == 's' && computerChoice == 'p')) {
        return "You win!";
    } else {
        return "Computer wins!";
    }
}

int main() {
    srand(time(0)); // Seed the random number generator

    cout << "Welcome to Rock-Paper-Scissors game!" << endl;
    bool playAgain = true;
    while (playAgain) {
        char userChoice = getUserChoice();
        char computerChoice = getComputerChoice();
        cout << "You chose: ";
        if (userChoice == 'r') cout << "rock" << endl;
        else if (userChoice == 'p') cout << "paper" << endl;
        else if (userChoice == 's') cout << "scissors" << endl;
        cout << "Computer chose: ";
        if (computerChoice == 'r') cout << "rock" << endl;
        else if (computerChoice == 'p') cout << "paper" << endl;
        else if (computerChoice == 's') cout << "scissors" << endl;
        cout << determineWinner(userChoice, computerChoice) << endl;

        // Ask user if they want to play again
        cout << "Do you want to play again? (yes/no): ";
        string playAgainInput;
        cin >> playAgainInput;
        if (playAgainInput != "yes") {
            playAgain = false;
        }
    }
    return 0;
}
