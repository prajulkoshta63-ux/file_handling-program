# file_handling-program
#file handling
#Create a file employee.txt and store 5 employee names entered by the user.
print("=" * 20)
print("/n Create a file employee.txt and store 5 employee names entered by the user:")
print("=" * 20)
with open("employee.txt", "w") as file:
    for i in range(5):
        name = input("Enter employee name: ")
        file.write(name + "\n")
#Read and display complete content of employee.txt file.
print("=" * 20)
print("/n Read and display complete content of employee.txt file:")
print("=" * 20)
with open("employee.txt", "r") as file:
    content = file.read()
    print(content)
file.close()
#count total characters persent in a file.
print("=" * 20)
print("/n Count total characters present in a file:")
print("=" * 20)
with open("employee.txt", "r") as file:
    content = file.read()
    character_count = len(content)
    print("Total characters in employee.txt:", character_count)
file.close()
#count total words present in a file.
print("=" * 20)
print("/n Count total words present in a file:")
print("=" * 20)
with open("employee.txt", "r") as file:
    content = file.read()
    words = content.split()
    word_count = len(words)
    print("Total words in employee.txt:", word_count)
file.close()
#count total lines present in a file.
print("=" * 20)
print("/n Count total lines present in a file:")
print("=" * 20)
with open("employee.txt", "r") as file:
    lines = file.readlines()
    line_count = len(lines)
    print("Total lines in employee.txt:", line_count)
file.close()
#read line by line
print("=" * 20)
print("/n Read line by line:")
print("=" * 20)
with open("employee.txt", "r") as file:
    for line in file:
        print(line.strip())
file.close()
#add 2 new records in an existing file employee.txt without deleting old data.
print("=" * 20)
print("/n Add 2 new records in an existing file employee.txt without deleting old data:")
print("=" * 20)
with open("employee.txt", "a") as file:
    for i in range(2):
        name = input("Enter new employee name: ")
        file.write(name + "\n")
file.close()
# check whether a file exists or not.
print("=" * 20)
print("/n Check whether a file exists or not:")
print("=" * 20)
import os
filename = "employee.txt"
if os.path.isfile(filename):
    print(f"{filename} exists.")
else:
    print(f"{filename} does not exist.")

# Count total vowels present in a file.

file = open("employee.txt", "r")

data = file.read()

count = 0

for ch in data:
    if ch in "aeiouAEIOU":
        count += 1

print("Total Vowels =", count)

file.close()

# Count uppercase and lowercase characters separately.

file = open("employee.txt", "r")


data = file.read()

upper = 0
lower = 0

for ch in data:
    if ch.isupper():
        upper += 1
    elif ch.islower():
        lower += 1

print("Uppercase =", upper)
print("Lowercase =", lower)

file.close()

# Find the longest line in a text file.

file = open("employee.txt", "r")

lines = file.readlines()

longest = ""

for line in lines:
    if len(line) > len(longest):
        longest = line

print("Longest Line:", longest)

file.close()

# Copy content of one file to another.

source = open("employee.txt", "r")
data = source.read()
source.close()

dest = open("copy.txt", "w")
dest.write(data)
dest.close()

print("File Copied Successfully")

# Replace all occurrences of "Python" with "Programming".

file = open("employee.txt", "r")

data = file.read()

file.close()

data = data.replace("Python", "Programming")

file = open("employee.txt", "w")

file.write(data)

file.close()

# Store marks of students and display students scoring more than 75.

file = open("marks.txt", "w")

for i in range(3):
    name = input("Enter Name: ")
    marks = input("Enter Marks: ")
    file.write(name + "," + marks + "\n")

file.close()

file = open("marks.txt", "r")

for line in file:
    name, marks = line.strip().split(",")

    if int(marks) > 75:
        print(name, marks)

file.close()

# Store employee records in a binary file and search by EmpID.

import pickle

file = open("employee.dat", "wb")

for i in range(3):
    empid = int(input("Enter EmpID: "))
    name = input("Enter Name: ")

    record = [empid, name]

    pickle.dump(record, file)

file.close()

search_id = int(input("Enter EmpID to Search: "))

file = open("employee.dat", "rb")

found = False

try:
    while True:
        record = pickle.load(file)

        if record[0] == search_id:
            print("Record Found:", record)
            found = True

except EOFError:
    pass

if not found:
    print("Record Not Found")

file.close()

file = open("employee.txt", "r")

count = 0

for line in file:
    if line.strip() == "":
        count += 1

print("Blank Lines =", count)

file.close()

file = open("employee.txt", "r")

data = file.read()

digits = 0
alphabets = 0
special = 0

for ch in data:
    if ch.isdigit():
        digits += 1
    elif ch.isalpha():
        alphabets += 1
    else:
        special += 1

print("Digits =", digits)
print("Alphabets =", alphabets)
print("Special Characters =", special)

file.close()


file = open("employee.txt", "r")

for line in file:
    text = line.strip()

    if text != "" and text[0].lower() in "aeiou":
        print(text)

file.close()

file = open("employee.txt", "r")

data = file.read().lower()

word = input("Enter word: ").lower()

count = data.split().count(word)

print("Frequency =", count)

file.close()

file = open("result.txt", "w")

for i in range(3):
    name = input("Enter Name: ")
    phy = int(input("Physics Marks: "))
    chem = int(input("Chemistry Marks: "))
    maths = int(input("Maths Marks: "))

    file.write(f"{name},{phy},{chem},{maths}\n")

file.close()

file = open("result.txt", "r")

topper = ""
highest = 0

for line in file:
    name, phy, chem, maths = line.strip().split(",")

    total = int(phy) + int(chem) + int(maths)

    if total > highest:
        highest = total
        topper = name

print("Topper =", topper)
print("Total Marks =", highest)

file.close()
