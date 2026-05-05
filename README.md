# Open the file
file = open("CS4.txt", "r")

# ---------- Task 1: Basic File Reading ----------
content = file.read()
file.seek(0)

lines = file.readlines()

print("Total number of lines:", len(lines))

print("\nFirst 2 lines:")
for line in lines[:2]:
    print(line.strip())

print("\nLast 2 lines:")
for line in lines[-2:]:
    print(line.strip())


# ---------- Task 2: Log Classification ----------
file.seek(0)

counts = {
    "INFO": 0,
    "WARNING": 0,
    "ERROR": 0
}

for line in lines:
    if "INFO" in line:
        counts["INFO"] += 1
    if "WARNING" in line:
        counts["WARNING"] += 1
    if "ERROR" in line:
        counts["ERROR"] += 1

print("\nLog Counts:")
print(counts)


# ---------- Task 3: Write Filtered Files ----------
info_file = open("info_logs.txt", "w")
warning_file = open("warning_logs.txt", "w")
error_file = open("error_logs.txt", "w")

for line in lines:
    if "INFO" in line:
        info_file.write(line)
    if "WARNING" in line:
        warning_file.write(line)
    if "ERROR" in line:
        error_file.write(line)

info_file.close()
warning_file.close()
error_file.close()


# ---------- Task 4: Search Feature ----------
keyword = input("\nEnter keyword to search (INFO/WARNING/ERROR): ")

search_file = open("search_result.txt", "w")

print("\nMatching lines:")
for line in lines:
    if keyword in line:
        print(line.strip())
        search_file.write(line)

search_file.close()


# ---------- File Pointer Operations ----------
file.seek(0)

print("\nFirst 50 characters:")
print(file.read(50))

file.seek(0)
print("\nFrom beginning again:")
print(file.read(50))

# Move to middle
file.seek(len(content)//2)
print("\nFrom middle:")
print(file.read(50))

# Last 100 characters
file.seek(-100, 2)
print("\nLast 100 characters:")
print(file.read())

file.close()
