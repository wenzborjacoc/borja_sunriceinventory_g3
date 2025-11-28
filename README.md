inventory = []

while True:
    print("\nInventory Management System")
    print("+----+------------------------------------+")
    print("| No |              Action                |")
    print("+----+------------------------------------+")
    print("| 1  | Add Product (Sack of Rice)         |")
    print("| 2  | Update Product                     |")
    print("| 3  | Delete Product                     |")
    print("| 4  | Search Product                     |")
    print("| 5  | View All Products                  |")
    print("| 6  | Exit                               |")
    print("+----+------------------------------------+")

    choice = input("Select an option (1-6): ")

    if choice == '1':
        name = input("Enter rice type: ")

        quantity = int(input("Enter quantity in sacks: "))
        while quantity <= 0:
            if quantity == 0:
                print("1 is the minimum value allowed.")
            else:
                print("Please enter a positive number.")
            quantity = int(input("Enter quantity in sacks: "))

        reorder = int(input("Enter reorder level in sacks: "))
        while reorder <= 0:
            if reorder == 0:
                print("1 is the minimum value allowed.")
            else:
                print("Please enter a positive number.")
            reorder = int(input("Enter reorder level in sacks: "))

        inventory.append([name, quantity, reorder])
        print(f"Added {quantity} sacks of '{name}'.")

    elif choice == '2':
        if not inventory:
            print("No products in inventory.")
        else:
            print("\nCurrent Inventory:")
            print("+------------------+----------------+----------------------+")
            print("| Rice Type        | Quantity       | Reorder Level        |")
            print("+------------------+----------------+----------------------+")
            for item in inventory:
                print(f"| {item[0]:<16} | {item[1]:<14} | {item[2]:<20} |")
            print("+------------------+----------------+----------------------+")

            name = input("Enter rice type to update: ")
            for item in inventory:
                if item[0] == name:
                    new_quantity = int(input("Enter new quantity in sacks: "))
                    while new_quantity <= 0:
                        if new_quantity == 0:
                            print("1 is the minimum value allowed.")
                        else:
                            print("Please enter a positive number.")
                        new_quantity = int(input("Enter new quantity in sacks: "))

                    new_reorder = int(input("Enter new reorder level in sacks: "))
                    while new_reorder <= 0:
                        if new_reorder == 0:
                            print("1 is the minimum value allowed.")
                        else:
                            print("Please enter a positive number.")
                        new_reorder = int(input("Enter new reorder level in sacks: "))

                    item[1] = new_quantity
                    item[2] = new_reorder
                    print(f"{name}' updated successfully!")
                    break
            else:
                print("Rice type not found.")

    elif choice == '3':
        if not inventory:
            print("No products to delete.")
        else:
            print("\nCurrent Inventory:")
            print("+------------------+----------------+----------------------+")
            print("| Rice Type        | Quantity       | Reorder Level        |")
            print("+------------------+----------------+----------------------+")
            for item in inventory:
                print(f"| {item[0]:<16} | {item[1]:<14} | {item[2]:<20} |")
            print("+------------------+----------------+----------------------+")

            name = input("Enter rice type to delete: ")
            for item in inventory:
                if item[0] == name:
                    inventory.remove(item)
                    print(f"🗑️ Deleted '{name}'.")
                    break
            else:
                print("Rice type not found.")

    elif choice == '4':
        name = input("Enter rice type to search: ")
        for item in inventory:
            if item[0] == name:
                print(f"Found: {item[0]} - Quantity: {item[1]} sacks, Reorder Level: {item[2]} sacks")
                break
        else:
            print("Product not found.")

    elif choice == '5':
        if not inventory:
            print("No products in inventory.")
        else:
            print("\nInventory Report:")
            print("+------------------+----------------+----------------------+")
            print("| Rice Type        | Quantity       | Reorder Level        |")
            print("+------------------+----------------+----------------------+")
            for item in inventory:
                print(f"| {item[0]:<16} | {item[1]:<14} | {item[2]:<20} |")
            print("+------------------+----------------+----------------------+")

    elif choice == '6':
        print(" Exiting the Inventory Management System.")
        break

    else:
        print("Invalid choice. Please try again.")

