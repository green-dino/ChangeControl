```python
class PythonStringManipulation:
    def __init__(self, input_string):
        self.s = input_string

    def display_info(self):
        print("\nPython String\n")
        print("characters: ", len(self.s))
        print("capitalize:", self.s.capitalize())
        print("upper case:", self.s.upper())
        print("lower case:", self.s.lower())
        print("Count o:   ", self.s.count('o'))

    def slice_string(self):
        print("s[0,4] : ", self.s[0:4])
        print("s[8:]  : ", self.s[8:])
        print("s[9:12]: ", self.s[9:12])

    def search_substring(self):
        if 'brown' in self.s:
            print("Found brown")
        else:
            print("brown Not Found")

        if 'Brown' in self.s:
            print("Found Brown")
        else:
            print("Brown Not Found")

        if 'BROWN' in self.s.upper():
            print("Found BROWN")
        else:
            print("BROWN Not Found")

    def split_string(self):
        string_split = self.s.split()
        print("Strings: ", len(string_split))
        print("s.split returns :", type(string_split))
        print("s.split: ", string_split)
        string_split.sort()
        print("s.split Sorted: ", string_split)

    def ordinal_value(self):
        print("The Ordinal Value of the first character: ", ord(self.s[0]))

    def check_endswith(self):
        if self.s.endswith('dog'):
            print("String ends with dog")
        else:
            print("String does not end with dog")

        if self.s.endswith('cat'):
            print("String ends with cat")
        else:
            print("String does not end with cat")


# Example usage:
input_string = "the quick brown fox jumps over the lazy dog"
string_manipulation = PythonStringManipulation(input_string)
string_manipulation.display_info()
string_manipulation.slice_string()
string_manipulation.search_substring()
string_manipulation.split_string()
string_manipulation.ordinal_value()
string_manipulation.check_endswith()

```