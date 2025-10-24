# password-strength-checker
Python project to check password strength and hash passwords
import re

def check_password_strength(password):
  
    length_error = len(password) < 8
    uppercase_error = re.search(r"[A-Z]", password) is None
    lowercase_error = re.search(r"[a-z]", password) is None
    digit_error = re.search(r"\d", password) is None
    special_char_error = re.search(r"[!@#$%^&*(),.?\":{}|<>]", password) is None

   
    errors = sum([length_error, uppercase_error, lowercase_error, digit_error, special_char_error])

    if errors == 0:
        strength = "Strong 💪"
    elif errors <= 2:
        strength = "Moderate 😐"
    else:
        strength = "Weak 😞"

   
    print("\nPassword Analysis:")
    print(f"Length OK: {not length_error}")
    print(f"Uppercase OK: {not uppercase_error}")
    print(f"Lowercase OK: {not lowercase_error}")
    print(f"Digit OK: {not digit_error}")
    print(f"Special Character OK: {not special_char_error}")
    print(f"\nPassword Strength: {strength}")

    return strength


if __name__ == "__main__":
    pwd = input("Enter your password: ")
    check_password_strength(pwd)

