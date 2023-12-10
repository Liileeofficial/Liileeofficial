 investment==
    def __init__(self, name, symbol, price):
        self.name = name
        self.symbol = symbol
        self.price = price
        self.quantity = 0

    def buy(self, quantity):
        self.quantity += quantity

    def sell(self, quantity):
        if quantity <= self.quantity:
            self.quantity -= quantity
        else:
            print("Not enough shares to sell.")

    def calculate_value(self):
        return self.quantity * self.price


class Portfolio:
    def __init__(self):
        self.investments = []

    def add_investment(self, investment):
        self.investments.append(investment)

    def calculate_total_value(self):
        total_value = 0
        for investment in self.investments:
            total_value += investment.calculate_value()
        return total_value


# Example usage:

if __name__ == "__main__":
    # Create investments
    apple_stock = Investment("Apple Inc.", "AAPL", 150.0)
    google_stock = Investment("Alphabet Inc.", "GOOGL", 2800.0)

    # Create a portfolio
    my_portfolio = Portfolio()

    # Add investments to the portfolio
    my_portfolio.add_investment(apple_stock)
    my_portfolio.add_investment(google_stock)

    # Buy and sell some shares
    apple_stock.buy(10)
    google_stock.buy(5)

    apple_stock.sell(3)
    google_stock.sell(2)

    # Calculate and print the total portfolio value
    total_value = my_portfolio.calculate_total_value()
    print(f"Total Portfolio Value: ${total_value}")
