# Excercise 1 Directory Structure

```python
import os
from time import ctime

class FileDetails:
    def __init__(self, file_type, file_name, size=None, modification_time=None):
        self.file_type = file_type
        self.file_name = file_name
        self.size = size
        self.modification_time = modification_time

def get_current_working_directory():
    print("Current Working Directory")
    print(os.getcwd())

def list_file_names(directory="."):
    print("List of File Names")
    fileList = os.listdir(directory)

    for eachFile in fileList:
        print(eachFile)

def print_file_types(file_list):
    print("File and Type")
    for eachFile in file_list:
        if os.path.isdir(eachFile):
            print("DIR:  ", eachFile)
        elif os.path.isfile(eachFile):
            print("FILE: ", eachFile)
        elif os.path.islink(eachFile):
            print("LINK: ", eachFile)
        elif os.path.ismount(eachFile):
            print("MNT:  ", eachFile)
        else:
            print("UNKNOWN: ", eachFile)

def store_and_print_file_details(directory="."):
    print("Store File Details in a List, Sort and Print")
    file_details = []
    for eachFile in os.listdir(directory):
        stats = os.stat(eachFile)
        mTime = stats.st_mtime
        mTime = ctime(mTime)
        fSize = stats.st_size

        if os.path.isdir(eachFile):
            file_details.append(FileDetails("DIR", eachFile))
        elif os.path.isfile(eachFile):
            file_details.append(FileDetails("FILE", eachFile, fSize, mTime))
        elif os.path.islink(eachFile):
            file_details.append(FileDetails("LINK", eachFile, fSize, mTime))
        elif os.path.ismount(eachFile):
            file_details.append(FileDetails("MNT", eachFile, fSize, mTime))

    file_details.sort(key=lambda x: x.file_name)

    for eachItem in file_details:
        print(f"{eachItem.file_type}: {eachItem.file_name}")

def extract_additional_file_details(directory="."):
    print("Extract additional file details")
    file_details = []
    for eachFile in os.listdir(directory):
        stats = os.stat(eachFile)
        mTime = stats.st_mtime
        mTime = ctime(mTime)
        fSize = stats.st_size

        if os.path.isdir(eachFile):
            file_details.append(FileDetails("DIR", eachFile, fSize, mTime))
        elif os.path.isfile(eachFile):
            file_details.append(FileDetails("FILE", eachFile, fSize, mTime))
        elif os.path.islink(eachFile):
            file_details.append(FileDetails("LINK", eachFile, fSize, mTime))
        elif os.path.ismount(eachFile):
            file_details.append(FileDetails("MNT", eachFile, fSize, mTime))

    file_details.sort(key=lambda x: x.file_name)

    for eachItem in file_details:
        print(f"{eachItem.file_type}: {eachItem.file_name}, Size: {eachItem.size}, Modification Time: {eachItem.modification_time}")

def walk_and_print_relative_path(directory="."):
    print("Walk the Path and print the relative path")
    for root, dirs, files in os.walk(directory):
        for file in files:
            relativePath = os.path.join(root, file)
            print(relativePath)

# Example Usage
get_current_working_directory()
print("=========================================\n")
list_file_names()
print("=========================================\n")
print_file_types(os.listdir("."))
print("=========================================\n")
store_and_print_file_details()
print("=========================================\n")
extract_additional_file_details()
print("=========================================\n")
walk_and_print_relative_path()
```