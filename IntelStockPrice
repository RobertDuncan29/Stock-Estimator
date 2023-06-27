import matplotlib.pyplot as plt
import random

stockHistory = open("Intel Stock Prices last 3Y.txt")

previous36MonthStockPrice = []

for line in stockHistory:
    price = ""
    for i in range(len(line)):
        price = price + line[i]
        if line[i] == ".":
            price = price + line[i + 1] + line[i + 2]
            previous36MonthStockPrice.append(float(price))
            break

x = range(1, 37)
y = previous36MonthStockPrice
plt.plot(x, y)
plt.xticks(x)
plt.xticks(rotation=90)
plt.xlabel('Dates for 36 Month History')
plt.ylabel('Stock Price for Previous 36 Months')
plt.title('Intel Stock Price Last 36 Months')
plt.show()
plt.savefig('Intel Previous 36 Month Stock Data.png')

initialInvestment = 100000
stocksHeld = int(initialInvestment / previous36MonthStockPrice[35])
returnOnInvestment = []

iterations = input("How many Iterations do you want to run? ")
iterations = int(iterations)

for iteration in range(iterations):
    percentChangeLast36Month = []
    for i in range(len(previous36MonthStockPrice) - 1):
        percent = ((previous36MonthStockPrice[i + 1] - previous36MonthStockPrice[i]) / previous36MonthStockPrice[i] * 100)
        percentChangeLast36Month.append(round(percent, 2))
    newPriceNext36Month = []
    lastMonthStockPrice = previous36MonthStockPrice[35]
    for i in range(36):
        percentChange = random.choice(percentChangeLast36Month)
        newPrice = lastMonthStockPrice + (lastMonthStockPrice * (percentChange / 100))
        lastMonthStockPrice = round(newPrice, 2)
        newPriceNext36Month.append(round(newPrice, 2))
    returnOnInvestment.append(newPriceNext36Month[35] * stocksHeld)
    x = range(1, 37)
    y = newPriceNext36Month
    plt.plot(x, y)
    plt.xticks(x)
    plt.xticks(rotation=90)
    plt.xlabel('Dates for Next 36 Months')
    plt.ylabel('Stock Price for Next 36 Months')
    plt.title('Intel Stock Price Next 36 Months')
    plt.show()
    plt.savefig('Intel Next 36 Month Stock Data.png')

for i in range(len(returnOnInvestment)):
    print("With an Investment of ${}, after iteration {}, you would have ${}"
          " resulting in a net change of ${}".format(initialInvestment, i + 1, returnOnInvestment[i],
                                                     (returnOnInvestment[i] - initialInvestment)))
