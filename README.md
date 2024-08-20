# hackathon2
class Auction:
    def __init__(self, item, current_bid):
        self.item = item
        self.current_bid = current_bid

    def place_bid(self, bid_amount):
        if bid_amount > self.current_bid:
            self.current_bid = bid_amount
            print(f"Bid accepted! New current bid for {self.item} is ${self.current_bid}.")
        else:
            print(f"Bid rejected! Your bid of ${bid_amount} must be greater than the current bid of ${self.current_bid}.")

def display_auctions(auctions):
    print("\nAvailable Auctions:")
    for idx, auction in enumerate(auctions):
        print(f"{idx + 1}. {auction.item} - Current Bid: ${auction.current_bid}")

def main():
    # Sample data for auctions
    auctions = [
        Auction("Antique Vase", 50),
        Auction("Vintage Watch", 150),
    ]

    while True:
        display_auctions(auctions)

        try:
            choice = int(input("\nSelect an auction to bid on (1 or 2), or 0 to exit: "))
            if choice == 0:
                print("Exiting the auction system.")
                break
            elif 1 <= choice <= len(auctions):
                selected_auction = auctions[choice - 1]
                bid_amount = float(input(f"Enter your bid for {selected_auction.item}: "))
                selected_auction.place_bid(bid_amount)
            else:
                print("Invalid choice. Please select a valid auction number.")
        except ValueError:
            print("Invalid input. Please enter a number.")

if __name__ == "__main__":
    main()


