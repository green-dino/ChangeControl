# Excercise 4 Objects 

```python
import hashlib
import os
import sys
import time

class FileHasher:

    VALID_HASH_TYPES = ['MD5', 'SHA1', 'SHA256', 'SHA512']

    def __init__(self):
        ''' Create object variables and Constants '''
        self.filePath = ''
        self.fileSize = ''
        self.modifiedTime = ''
        self.createTime = ''
        self.fileHash = ''
        self.hashType = ''
        self.lastErr = ''

    def set_file_path(self, file_path):
        ''' Set the file path if valid 
            Obtain file size and timestamps
            return True if valid and set the self.filePath object variable
        '''
        if os.path.isfile(file_path):
            if os.access(file_path, os.R_OK):
                self.filePath = file_path
                stats = os.stat(self.filePath)
                self.fileSize = stats.st_size
                self.modifiedTime = time.ctime(stats.st_mtime)
                self.createTime = time.ctime(stats.st_atime)
                self.lastErr = ''
                return True
            else:
                self.filePath = ''
                self.lastErr = 'Invalid File Path'
                return False
        else:
            self.filePath = ''
            self.lastErr = 'Not a File'
            return False

    def set_hash_type(self, hash_type):
        ''' Set the Hash Type verify it is supported '''
        if hash_type in self.VALID_HASH_TYPES:
            self.hashType = hash_type
            self.lastErr = ''
            return True
        else:
            self.hashType = ''
            self.lastErr = 'Invalid Hash Type'
            return False

    def initialize_hash_object(self):
        if self.hashType == 'MD5':
            return hashlib.md5()
        elif self.hashType == 'SHA1':
            return hashlib.sha1()
        elif self.hashType == 'SHA256':
            return hashlib.sha256()
        elif self.hashType == 'SHA512':
            return hashlib.sha512()
        else:
            return hashlib.md5()

    def hash_file(self):
        ''' Using the object variables hash the file '''
        try:
            if self.hashType:
                hash_obj = self.initialize_hash_object()
            else:
                self.lastErr = 'Hash Type not Set'
                return False
            with open(self.filePath, 'rb') as file_to_hash:
                file_contents = file_to_hash.read()
                hash_obj.update(file_contents)
                self.fileHash = hash_obj.hexdigest()
                self.lastErr = ''
                return True
        except Exception as err:
            self.lastErr = str(err)
            return False

def main():
    print("Hash File Class Demonstration\n")

    if sys.version_info[0] < 3:
        file_name = raw_input("Enter file to hash: ")
    else:
        file_name = input("Enter file to hash: ")

    obj = FileHasher()

    print("\nProcessing File ...\n")

    if obj.set_file_path(file_name):
        if obj.set_hash_type('SHA256'):
            if obj.hash_file():
                print("Path:               ", obj.filePath)
                print("File Size:          ", '{:,}'.format(obj.fileSize), "Bytes")
                print("File Created Time:  ", obj.createTime)
                print("File Modified Time: ", obj.modifiedTime)
                print("Hash Type:          ", obj.hashType)
                print("Hash Value:         ", obj.fileHash)
            else:
                print("Hashing Failed: ", obj.lastErr)
        else:
            print("Failed to Set HashType: ", obj.lastErr)
    else:
        print("File Name Err: ", obj.lastErr)

    print("\nScript End")

if __name__ == "__main__":
    main()
```