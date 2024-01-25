# Excercise 3 File Paths

```python title="filepath.py"
import hashlib
import sys

class FileHasher:
    def __init__(self):
        if sys.version_info[0] < 3:
            self.PYTHON_2 = True
        else:
            self.PYTHON_2 = False

    def hash_file(self, file_path):
        '''
        function takes one input a valid filePath
        returns the hexdigest of the file
        or error
        '''
        try:
            with open(file_path, 'rb') as file_to_hash:
                file_contents = file_to_hash.read()
                hash_obj = hashlib.md5()
                hash_obj.update(file_contents)
                digest = hash_obj.hexdigest()
                return digest
        except Exception as err:
            return str(err)

    def demonstrate_hash_file(self):
        print("Hash File Function Demonstration")

        if self.PYTHON_2:
            file_name = raw_input("Enter file to hash: ")
        else:
            file_name = input("Enter file to hash: ")

        hex_digest = self.hash_file(file_name)
        print(hex_digest)

def main():
    file_hasher = FileHasher()
    file_hasher.demonstrate_hash_file()

if __name__ == "__main__":
    main()

```