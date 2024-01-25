```python
from __future__ import print_function

class PythonListsDemo:
    def __init__(self):
        self.empty_list = []

    def simple_list_demo(self):
        print("Simple Demonstration of Lists in Python")
        print("=======================================")
        print()

        # Create an empty list
        print("Empty List ", self.empty_list)
        print()

        # Create a list with initial values
        test_list = ['Suspect', 'Witness', 'Victim']
        print("Initialized List ", test_list)
        print()

        # Append a value to a list
        test_list.append("Accomplice")
        print("Appended List ", test_list)
        print()

        # Insert a value into the list
        test_list.insert(2, "Informant")
        print("Inserted List ", test_list)
        print()

        # Pop a value off the list
        pop_value = test_list.pop()
        print("Value Popped from List ", pop_value)
        print("New List ", test_list)
        print()

        # Iterate through the list
        print("Iterate through the list")
        for value in test_list:
            print(value)
        print()

        # Sorting a list
        test_list.sort()
        print("Sorted List = ", test_list)
        print()

    def complex_list_demo(self):
        complex_list = ["John Doe", ["Age", 50], ["Height", 5, 6]]
        for each_item in complex_list:
            print(each_item)

        for each_item in complex_list:
            if isinstance(each_item, list):
                for each_value in each_item:
                    print(each_value, end=" ")
                print()
            else:
                print(each_item)


# Example usage:
python_lists_demo = PythonListsDemo()
python_lists_demo.simple_list_demo()
print("\nLab-3 Python Lists\n")
python_lists_demo.complex_list_demo()
```