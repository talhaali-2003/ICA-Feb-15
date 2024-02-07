# Revision number 02/07/2024
## Begin Talha Ali (02/07/2024) 

import random
import string

# Example dictionary list (in a real scenario, this would be much larger)
dictionary_words = ['password', 'admin', 'guest', 'user', 'root']

# Characters that can be used in the passwords
lowercase_letters = string.ascii_lowercase
uppercase_letters = string.ascii_uppercase
digits = string.digits
special_symbols = "!@#$%^&*()-_=+"

# Password requirements
min_length = 8  # Minimum password length
max_length = 12  # Maximum password length

# Function to create a random password
def create_random_password():
    length = random.randint(min_length, max_length)
    password_characters = lowercase_letters + uppercase_letters + digits + special_symbols
    password = ''.join(random.choice(password_characters) for i in range(length))
    return password

# Function to check if password is acceptable
def is_acceptable(password):
    return any(char in special_symbols for char in password) and password not in dictionary_words

# Main password simulator function
def password_simulator(iterations=40):
    archived_passwords = []

    for i in range(iterations):
        password = create_random_password()
        if is_acceptable(password):
            archived_passwords.append(password)
            print(f"Password accepted and archived: {password}")
        else:
            print(f"Password rejected: {password}")
    
    return archived_passwords

# Run the password simulator
archived_passwords = password_simulator()

print("\nArchived Passwords:")
for passwd in archived_passwords:
    print(passwd)


# Revision number 02/07/2024
## End Talha Ali
# SE1 Group 3