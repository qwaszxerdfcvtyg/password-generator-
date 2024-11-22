import random
import string

def generate_password(length=12):
    """
    Generates a random password with the given length.
    
    :param length: Length of the password (default is 12)
    :return: A randomly generated password
    """
    if length < 6:
        print("Password length should be at least 6 characters.")
        return None

    # Define character sets
    lower = string.ascii_lowercase
    upper = string.ascii_uppercase
    digits = string.digits
    special = string.punctuation

    # Ensure the password has at least one character from each set
    all_chars = lower + upper + digits + special
    password = [
        random.choice(lower),
        random.choice(upper),
        random.choice(digits),
        random.choice(special)
    ]

    # Fill the remaining characters randomly
    password += random.choices(all_chars, k=length - 4)

    # Shuffle to make it more random
    random.shuffle(password)

    return ''.join(password)

# User input for password length
try:
    length = int(input("Enter the desired length for your password (minimum 6): "))
    password = generate_password(length)
    if password:
        print(f"Generated Password: {password}")
except ValueError:
    print("Invalid input! Please enter a numeric value.")
