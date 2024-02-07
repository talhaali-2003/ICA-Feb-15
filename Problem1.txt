# Revision number 02/07/2024
## Begin Talha Ali (02/07/2024) 

import random
import string
from datetime import datetime, timedelta

# General Requirements for Data Simulation
NUM_USERS = 100  # Number of sample users to generate
STATES = ['NY', 'CA', 'FL', 'TX', 'PA', 'IL', 'OH']  # Example states
PRODUCTS = ['ID-product1', 'ID-product2', 'ID-product3']  # Example products
SALESPERSONS = ['ID-sales1', 'ID-sales2', 'ID-sales3']  # Example salespersons

# Step One: 'data collector'
def generate_random_date():
    start_date = datetime(1970, 1, 1)
    end_date = datetime(2000, 12, 31)
    time_between_dates = end_date - start_date
    random_number_of_days = random.randrange(time_between_dates.days)
    random_date = start_date + timedelta(days=random_number_of_days)
    return random_date.strftime("%Y-%m-%d")

def generate_random_ssn():
    return f"{random.randint(100, 999)}-{random.randint(10, 99)}-{random.randint(1000, 9999)}"

def generate_random_address():
    return f"{random.randint(100, 9999)} {random.choice(['Main', 'Oak', 'Pine', 'Maple', 'Cedar'])} St, {random.choice(STATES)}"

def create_user_data():
    user_data = {}
    for i in range(NUM_USERS):
        user_id = f"ID-{random.randint(1000, 9999)}"
        user_data[user_id] = {
            'username': ''.join(random.choices(string.ascii_lowercase, k=8)),
            'password': ''.join(random.choices(string.ascii_letters + string.digits, k=10)),
            'birthdate': generate_random_date(),
            'address': generate_random_address(),
            'social_security_number': generate_random_ssn(),
            'productPurchased': random.choice(PRODUCTS),
            'salesperson': random.choice(SALESPERSONS)
        }
    return user_data

# Step Two: 'key/value' pairs are already in a Python dictionary from Step One

# Step Three: search engine
def search_data(data, key, value):
    results = [user_id for user_id, user_info in data.items() if value in user_info.get(key, '')]
    return results

# Simulate data warehousing
data_collector = create_user_data()

# Example searches within the Python code
state_search = search_data(data_collector, 'address', 'CA')  # Search for users in California
salesperson_search = search_data(data_collector, 'salesperson', 'ID-sales1')  # Search for users handled by salesperson ID-sales1

# Display example search results
print(f"Users in California: {state_search}")
print(f"Users handled by salesperson ID-sales1: {salesperson_search}")


# Revision number 02/07/2024
## End Talha Ali
# SE1 Group 3
