# Rename multiple files' names in Linux by python

```python
import os 


def main(): 
    path = "~/whatever_path/"
    for filename in os.listdir(path):
        substrings = filename.split('_')
        part0 = substrings[0]
        part1 = substrings[1].split(".")[0]
        part2 = substrings[2].split(".csv")[0].split(".")[0]

        new_name = "{}_{}_{}.csv".format(part0, part1, part2)
        print(new_name)
    
        os.rename(path + filename, path + new_name)
  

if __name__ == '__main__': 
    main() 
```
