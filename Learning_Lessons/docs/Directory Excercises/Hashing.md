# Excercise 2 File Hashing

```python
import os
import hashlib

def calculate_file_hash(file_path):
    try:
        with open(file_path, "rb") as the_file:
            hash_obj = hashlib.sha256()
            chunk_size = 2**16
            
            while True:
                chunk = the_file.read(chunk_size)
                if len(chunk) > 0:
                    hash_obj.update(chunk)
                else:
                    return hash_obj.hexdigest()
    except Exception as e:
        print(f"Error calculating hash for {file_path}: {e}")
        return None

def hash_files_in_directory(directory="."):
    files_to_hash = os.listdir(directory)

    for each_file in files_to_hash:
        file_path = os.path.join(directory, each_file)
        
        if os.path.isfile(file_path):
            if os.access(file_path, os.R_OK):
                file_hash = calculate_file_hash(file_path)
                if file_hash:
                    print(each_file, file_hash)
            else:
                print(each_file, "Not Readable")
        else:
            print(each_file, "Not a File")

def main():
    directory_path = "."  # Change this to the desired directory path
    print(f"Hashing files in directory: {directory_path}")
    hash_files_in_directory(directory_path)

if __name__ == "__main__":
    main()
```