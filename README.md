# dynamic-expance-calculator
expenses = {
    "Food": 0.0,
    "Transport": 0.0,
    "Entertainment": 0.0,
    "Other": 0.0
}

def add_expense(category, amount):
    if category in expenses:
        expenses[category] += amount
    else:
        print(f"Invalid category '{category}'. Please choose from: {', '.join(expenses.keys())}")

def display_summary():
    total_expenses = sum(expenses.values())
    print("\nExpense Summary:")
    print("-" * 30)
    for category, amount in expenses.items():
        percentage = (amount / total_expenses * 100) if total_expenses > 0 else 0
        print(f"{category}: ${amount:.2f} ({percentage:.2f}%)")
    print(f"Total Expenses: ${total_expenses:.2f}")

def ask_expenses():
    while True:
        print("\nCategories: Food, Transport, Entertainment, Other")
        print("Type 'summary' to see the summary of expenses or 'exit' to quit.")
        user_input = input("Enter category and amount (e.g., 'Food 20'): ").strip()

        if user_input.lower() == 'summary':
            display_summary()
        elif user_input.lower() == 'exit':
            print("Exiting the Expense Tracker. Goodbye!")
            break
        else:
            try:
                category, amount = user_input.split()
                amount = float(amount)
                add_expense(category.capitalize(), amount)
                display_summary()
            except ValueError:
                print("Invalid input. Please enter in the format 'Category Amount' (e.g., 'Food 20').")

if _name_ == "_main_":
    ask_expenses()
