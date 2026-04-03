# 4.3-Project
4.3 Project
print("<Jaihea8080>")
import csv
from datetime import datetime

path = "C:\\PythonFiles\\ZooData.csv"

def insertData(path, data):
    try:
        with open(path, 'a', newline='') as csvfile:
            csvfile.write(data + '\n')
    except Exception as e:
        print("Error writing to file:", e)


def viewData(path):
    print("The file", path)
    try:
        with open(path, 'r') as csvfile:
            reader = csv.reader(csvfile)
            for row in reader:
                print(','.join(row))
    except Exception as e:
        print("Error reading file:", e)

def getInput():
    dates = []
    temps = []

    while True:
        date = input("Enter a date: ")
        if date == "":
            break
        dates.append(date)

        temp = input("Enter the highest temp for the inputted date: ")
        if temp == "":
            break
        temps.append(int(temp))

    for i in range(len(dates)):
        avg = sum(temps) / len(temps)
        data = dates[i] + "," + str(temps[i]) + "," + str(avg)
        try:
            insertData(path, data)
            print("The following data was saved at " + str(datetime.now()) + ":")
            print(data)
        except Exception as e:
            print("Error saving data:", e)

def main():
    print("=" * 60)
    print("Jaihea8080's Spreadsheet Automation Menu")
    print("Choose a number from the following options")
    print("1 Input Data")
    print("2 View Current Data")
    print("3 Generate Report")

    choice = input()
    print("You selected " + choice + " at " + str(datetime.now()))

    if choice == "1":
        getInput()
    elif choice == "2":
        viewData(path)
    elif choice == "3":
        print("Generating report...")
    else:
        print("Invalid selection")

main()
