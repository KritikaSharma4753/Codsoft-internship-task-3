#Codsoft-internship-task-3
import secrets
import string

def generate_password(length=12, use_lower=True, use_upper=True, use_digits=True, use_symbols=True):
    pool = ""
    if use_lower:  pool += string.ascii_lowercase
    if use_upper:  pool += string.ascii_uppercase
    if use_digits: pool += string.digits
    if use_symbols:pool += "!@#$%^&*()-_=+[]{};:,.<>?/\\|`~"  # you can change symbols if needed

    if not pool:
        raise ValueError("At least one character set must be enabled.")
    return ''.join(secrets.choice(pool) for _ in range(length))

# --- Example usage ---
try:
    n = int(input("Password length (e.g. 12): "))
    pwd = generate_password(length=n, use_lower=True, use_upper=True, use_digits=True, use_symbols=True)
    print("Generated password:", pwd)
except ValueError as e:
    print("Error:", e)
