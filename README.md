# Maths-Quiz-game
import random

# Define a function to generate a random math question
def generate_question():
    num1 = random.randint(1, 10)
    num2 = random.randint(1, 10)
    operation = random.choice(['+', '-', '*', '/'])
    
    if operation == '/':
        # Ensure the division results in an integer
        num1 = num1 * num2

    question = f"{num1} {operation} {num2}"
    answer = eval(question)
    return question, answer

# Define a function to get the player's answer
def get_answer(question):
    user_answer = input(f"Solve: {question} = ")
    return float(user_answer)

# Define a function to check the player's answer
def check_answer(correct_answer, user_answer):
    return correct_answer == user_answer

# Main game loop
def main():
    score = 0

    while True:
        # Generate a random math question
        question, correct_answer = generate_question()

        # Get the player's answer
        try:
            user_answer = get_answer(question)
        except ValueError:
            print("Please enter a valid number.")
            continue

        # Check if the answer is correct
        if check_answer(correct_answer, user_answer):
            print("Correct!")
            score += 1
        else:
            print(f"Incorrect. The correct answer was: {correct_answer}")

        # Ask the player if they want to play again
        play_again = input("Do you want to play again? (yes/no): ").lower()
        if play_again != 'yes':
            break

    print(f"Your final score is: {score}")

# Run the game
if __name__ == "__main__":
    main()
