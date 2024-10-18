#password complexity checker
import re

def check_password_strength(password):
    strength_score = 0
    feedback = []

    if len(password) >= 8:
        strength_score += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    if re.search(r'[A-Z]',password) and re.search(r'[a-z]', password):
        strength_score += 1
    else:
        feedback.append("Password should include both uppercase and lowercase letters.")

    if re.search(r'[0-9]', password):
        strength_score += 1
    else:
        feedback.append("Password should include at least one number.")

    if re.search(r'[@$!%*?&]', password):
        strength_score += 1
    else:
        feedback.append("Password should include at least one special character (e.g., @$!%*?&).")


    if strength_score == 4:
        return "Strong password! Your password meets all requirements."
    elif strength_score == 3:
        return "Moderate password. Consider improving it by adding missing requirements:\n" + "\n".join(feedback)
    else:
        return "Weak password. Please consider the following suggestions to improve:\n" + "\n".join(feedback)


password = input("Enter a password to check its strength: ")
result = check_password_strength(password)
print(result)
