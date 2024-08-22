# PRODIGY_cs_03
Password Complexity Checker
import re

def check_password_strength(password):
    # Criteria for password strength
    criteria = {
        "length": len(password) >= 8,
        "uppercase": re.search(r'[A-Z]', password) is not None,
        "lowercase": re.search(r'[a-z]', password) is not None,
        "number": re.search(r'[0-9]', password) is not None,
        "special_char": re.search(r'[!@#$%^&*(),.?":{}|<>]', password) is not None,
    }
    
    # Check how many criteria are met
    strength_score = sum(criteria.values())
    
    # Determine password strength
    if strength_score == 5:
        strength = "Very Strong"
    elif strength_score == 4:
        strength = "Strong"
    elif strength_score == 3:
        strength = "Moderate"
    elif strength_score == 2:
        strength = "Weak"
    else:
        strength = "Very Weak"

    # Feedback
    feedback = {
        "length": "Length (8+ characters): Passed" if criteria["length"] else "Length (8+ characters): Failed",
        "uppercase": "Uppercase letter: Passed" if criteria["uppercase"] else "Uppercase letter: Failed",
        "lowercase": "Lowercase letter: Passed" if criteria["lowercase"] else "Lowercase letter: Failed",
        "number": "Number: Passed" if criteria["number"] else "Number: Failed",
        "special_char": "Special character: Passed" if criteria["special_char"] else "Special character: Failed"
    }

    return strength, feedback

def main():
    print("Password Complexity Checker")
    password = input("Enter your password: ")
    
    strength, feedback = check_password_strength(password)
    
    print("\nPassword Strength:", strength)
    print("\nFeedback:")
    for key, value in feedback.items():
        print(value)

if __name__ == "__main__":
    main()
