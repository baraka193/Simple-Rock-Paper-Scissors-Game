import streamlit as st
import random

# ASCII Art
rock = """
    _______
---'   ____)
      (_____)
      (_____)
      (____)
---.__(___)
"""

paper = """
     _______
---'    ____)____
           ______)
          _______)
         _______)
---.__________)
"""

scissors = """
    _______
---'   ____)____
          ______)
       __________)
      (____)
---.__(___)
"""

# List of game images
game_images = [rock, paper, scissors]
choices = ["Rock", "Paper", "Scissors"]

# Title
st.title("✊✋✌ Rock-Paper-Scissors Game")

# Player choice
user_choice = st.radio("Choose your move:", options=[0, 1, 2], format_func=lambda x: choices[x])

if st.button("Play"):
    # Display player's choice
    st.subheader("You chose:")
    st.text(game_images[user_choice])

    # Computer's choice
    computer_choice = random.randint(0, 2)
    st.subheader("Computer chose:")
    st.text(game_images[computer_choice])

    # Game logic
    if user_choice >= 3 or user_choice < 0:
        result = "❌ Invalid choice. You lose!"
    elif user_choice == 0 and computer_choice == 2:
        result = "✅ You win!"
    elif computer_choice == 0 and user_choice == 2:
        result = "🤖 Computer wins!"
    elif computer_choice > user_choice:
        result = "🤖 Computer wins!"
    elif user_choice > computer_choice:
        result = "✅ You win!"
    elif computer_choice == user_choice:
        result = "🤝 It's a draw!"

    # Show result
    st.markdown(f"### {result}")
