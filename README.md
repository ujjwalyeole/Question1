# Question1
import re

def calculate_profanity(tweet, racial_slurs):
    words = tweet.lower().split()
    total_slurs = 0

    for word in words:
        # Remove punctuation marks from the word
        word = re.sub(r'[^\w\s]', '', word)
        
        if word in racial_slurs:
            total_slurs += 1

    # Calculate the degree of profanity based on the number of racial slurs found
    if total_slurs == 0:
        return "Clean"
    elif total_slurs == 1:
        return "Mild"
    elif total_slurs == 2:
        return "Moderate"
    else:
        return "High"

def main():
    # Assumption: The file contains one tweet per line
    file_path = "tweets.txt"
    
    # Assumption: The racial slurs are provided as a set of words
    racial_slurs = {"slur1", "slur2", "slur3"}

    with open(file_path, "r", encoding="utf-8") as file:
        for line in file:
            tweet = line.strip()
            profanity_degree = calculate_profanity(tweet, racial_slurs)
            print(f"Tweet: {tweet}")
            print(f"Profanity Degree: {profanity_degree}")
            print()

if __name__ == "__main__":
    main()
