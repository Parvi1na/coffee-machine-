# coffee-machine-
#-----------------My_code -------------
 if ask_menu == "report":
            resource_left = print(f"Water : {resources['water']}ml \nMilk: {resources['milk']}ml \nCoffee: {resources['coffee']}g \nMoney: ${profit}")
            coffee_serving()
            return resource_left
            
#-----------------Angela's -------------
    elif choice == "report":
        print(f"Water: {resources['water']}ml")
        print(f"Milk: {resources['milk']}ml")
        print(f"Coffee: {resources['coffee']}g")
        print(f"Money: ${profit}")
            
Точка улучшения: Масштабируемость
Подумайте о масштабируемости. Сделайте его динамическим, а не жестко запрограммированным. Меню напитков может быть изменено.

#-----------------My_code -------------
    while continue_serving:


        elif ask_menu == 'latte' or ask_menu == 'cappuccino' or ask_menu == 'espresso':
            execution
            
 #-----------------Angela's -------------
 
while is_on:


    else:
        drink = MENU[choice]
Точка улучшения: масштабируемость
Я попытался составить список ингредиентов, чтобы просмотреть каждый элемент, однако лучше использовать существующий словарь.
В коде Анджелы параметр order_ingredients — это словарь МЕНЮ[напитка], который имеет доступ к каждому ингредиенту. Предметы: молоко, кофе, молоко.
Этот метод гораздо более масштабируемый, даже если ингредиенты изменены, он все равно может обрабатываться независимо. Мой исходный код был жестко запрограммирован.

#------------My_code --------------------
def resource_check(drink, ingredient_type):
    ingredients_check = MENU[drink]['ingredients'][ingredient_type]
    resources_check = resources[ingredient_type]

    if ingredients_check <= resources_check:
        return True
    elif ingredients_check > resources_check:
        return False

def check(water_check, milk_check, coffee_check):

    if water_check:
        if milk_check:
            if coffee_check:
                print('Please insert coins.')
                return True
            else:
                print(f"Sorry there is not enough coffee.")
        else:
            print(f"Sorry there is not enough milk.")
    else:
        print(f"Sorry there is not enough water.")
    coffee_serving()
    
    
    
elif ask_menu == 'latte' or ask_menu == 'cappuccino' or ask_menu == 'espresso':  #resource checked #espresso doesn't have milk in dict, can I add it or should I make additional if statement
        water_check = resource_check(ask_menu, 'water')
        coffee_check = resource_check(ask_menu, 'coffee')
        milk_check = resource_check(ask_menu, 'milk')
        if check(water_check, milk_check, coffee_check):
    


#-----------------Angela's --------------------------
def is_resource_sufficient(order_ingredients):
    """Returns True when order can be made, False if ingredients are insufficient."""
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"Sorry there is not enough {item}.")
            return False
    return True
   drink = MENU[choice] #choice is user input 
 else:
    drink = MENU[choice]
    if is_resource_sufficient(drink["ingredients"]): #access to drink's dict
Подумайте, можно ли выполнить две операции в одной функции
process_coins()
Анжела обрабатывала две вещи в одной функции, тогда как я делал это по отдельности.

#------------My_code --------------------
def money(name_of_coins):
    ask_money = int(input(f"how many {name_of_coins}?: "))
    return ask_money
    
quarters = money("quarters")
                dimes = money("dimes")
                nickles = money("nickles")
                pennies = money("pennies")
user_money = round(0.25 * quarters + 0.1 * dimes + 0.05 * nickles + 0.01 * pennies, 2)
                change = round((user_money - MENU[ask_menu]["cost"]), 2)
     
     
#-----------------Angela's --------------------------     
def process_coins():
    """Returns the total calculated from coins inserted."""
    print("Please insert coins.")
    total = int(input("how many quarters?: ")) * 0.25
    total += int(input("how many dimes?: ")) * 0.1
    total += int(input("how many nickles?: ")) * 0.05
    total += int(input("how many pennies?: ")) * 0.01
    return total
Для циклов с параметром/аргументом словаря
параметр order_ingredients = MENU[выбор]['ингредиенты']
-> клавиша: молоко, кофе, вода внутри дикт. Каждая клавиша назначена элементу в цикле for.

#-----------------Angela's -------------------------- 
#1
def is_resource_sufficient(order_ingredients):
    """Returns True when order can be made, False if ingredients are insufficient."""
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"Sorry there is not enough {item}.")
            return False
    return True
    
    
drink = MENU[choice]   
if is_resource_sufficient(drink["ingredients"]): #argument: MENU dictionary


#2    
def make_coffee(drink_name, order_ingredients):
    """Deduct the required ingredients from the resources."""
    for item in order_ingredients:
        resources[item] -= order_ingredients[item]
    print(f"Here is your {drink_name} ☕️. Enjoy!")
    
make_coffee(choice, drink["ingredients"])
Мой окончательный код
Секрет в том, что... Мне пришлось изменить пункт в словаре, то есть молоко в эспрессо, из-за моих жестко закодированных строк.
Тем не менее, он работал нормально, за исключением этого. Я горжусь тем, что завершил его. Мой первый, почти 100 строк кода самостоятельно.
Для простоты мне нужно использовать циклы for в этом коде.
Всего у Анджелы было 90 строк кода, у меня 110.
Использование цикла может уменьшить объем кода.

Давайте добавим строки документации для каждой функции.
MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
            "milk": 0,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}

resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}
# TODO: 1. User input asking the menu
# TODO: 2. Turning off for maintenance
# TODO: 3. Check resources using report
# TODO: 4. Check enough resources to make coffee
def resource_check(drink, ingredient_type):
    ingredients_check = MENU[drink]['ingredients'][ingredient_type]
    resources_check = resources[ingredient_type]
if ingredients_check <= resources_check:
        return True
    elif ingredients_check > resources_check:
        return False
def check(water_check, milk_check, coffee_check):
if water_check:
        if milk_check:
            if coffee_check:
                print('Please insert coins.')
                return True
            else:
                print(f"Sorry there is not enough coffee.")
        else:
            print(f"Sorry there is not enough milk.")
    else:
        print(f"Sorry there is not enough water.")
    coffee_serving()
# TODO: 5. Input coins by user

def money(name_of_coins):
    ask_money = int(input(f"how many {name_of_coins}?: "))
    return ask_money
#
# TODO: 6. Calculate transaction
def calculate_transaction(money_insufficient, give_change, same, change):
    if money_insufficient:
        print("Sorry that's not enough money. Money refunded.")
        continue_serving = False
    elif give_change:
        print(f"Here is ${change} dollars in change.")
        return True
    elif same:
        return True
# TODO: 7. Add profit before making coffee
# TODO: 8-1. Make coffee deduct ingredients
def ingredients_deduction(drink, ingredient_type):
    resources[ingredient_type] -= MENU[drink]['ingredients'][ingredient_type]

#TODO: 8-2.  Print serving
#TODO: 10. serve the next customer by repeating from todo1

def coffee_serving():
    continue_serving = True
    profit = 0
    while continue_serving:
        ask_menu = input("What would you like? (espresso/latte/cappuccino): ").lower()
        if ask_menu == "report":
            print(f"Water : {resources['water']}ml \nMilk: {resources['milk']}ml \nCoffee: {resources['coffee']}g \nMoney: ${profit}")
        elif ask_menu == 'off':
            continue_serving == False
        elif ask_menu == 'latte' or ask_menu == 'cappuccino' or ask_menu == 'espresso':  #resource checked #espresso doesn't have milk in dict, can I add it or should I make additional if statement
            water_check = resource_check(ask_menu, 'water')
            coffee_check = resource_check(ask_menu, 'coffee')
            milk_check = resource_check(ask_menu, 'milk')
            if check(water_check, milk_check, coffee_check):
                quarters = money("quarters")
                dimes = money("dimes")
                nickles = money("nickles")
                pennies = money("pennies")

                user_money = round(0.25 * quarters + 0.1 * dimes + 0.05 * nickles + 0.01 * pennies, 2)
                print(user_money)

                change = round((user_money - MENU[ask_menu]["cost"]), 2)

                money_insufficient = (user_money < MENU[ask_menu]["cost"]) #bool True
                give_change = (user_money > MENU[ask_menu]["cost"])
                same = (user_money == MENU[ask_menu]["cost"])

                if calculate_transaction(money_insufficient, give_change, same, change): #enoug or same
                    profit += MENU[ask_menu]["cost"]
                    print(profit)

                    ingredients_deduction(ask_menu, 'milk')
                    ingredients_deduction(ask_menu, 'water')
                    ingredients_deduction(ask_menu, 'coffee')
                    print(resources)
                    print(f'Here is your {ask_menu} ☕ Enjoy!')
coffee_serving()


режим
перезаписи -мультикурсор: окно: Shift+Alt / Mac: опция+Shift






  
