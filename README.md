# Pig game(dice game which resets score when u roll a 1 and first to reach 20 wins)
import random

print('Enter no of players:')
n = input()

if n.isdigit():
    n = int(n)
else:
    print('Invalid input')
    exit()

scores = [0 for _ in range(n)]

while True:
    for i in range(n):
        print(f"\nPlayer {i+1}'s turn")
        turn_total = 0
        while True:
            dice = random.randint(1, 6)
            print('You rolled a', dice)

            if dice == 1:
                print("Oops! You rolled a 1. Turn over, no points this round.")
                turn_total = 0
                break
            else:
                turn_total += dice
                print(f"Turn total: {turn_total}, Overall score if held: {scores[i] + turn_total}")
                ans = input("Do you want to roll again? (y/n): ").lower()
                if ans != 'y':
                    break

        scores[i] += turn_total
        print(f"Your total score is {scores[i]}")

        if scores[i] >= 20:
            print(f"\nPlayer {i+1} wins!")
            print("Final scores:")
            for j in range(n):
                print(f"Player {j+1}: {scores[j]}")
            exit()
