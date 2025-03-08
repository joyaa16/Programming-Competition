# Introduction
Welcome to the CEC 2025 Programming Competition! Everything you need is in this Github, and we recommend the following steps to get started:

1. Read the rest of this README.md
2. Read the tutorial linked in githubHowToUseGithubDesktop.txt
3. Read the tutorial linked in githubHowToFork.txt
4. Fork this repo
5. Clone your forked repo locally on your machine
6. Start coding!

   
# Getting Help
Please follow the following steps if you need help:

1. Check the included documentation for logistics and scoring questions
2. Check the Programming Competition Case for competition questions
3. Check the discord for previously answered questions
4. If you have done all of that, ask the Directors for help. If we can answer your question, it will be posted on the discord in English and French.
   
# Important Notes
In your README.md please specify:

- How to run your code
- What language and version your code uses (ie. Python 3.11)
- A list of required packages (i.e. Pandas, NumPy), with version if needed (ie. pytorch==2.1.116)
- If needed, what OS your code should be run on Any specifications of this sort not included in your README cannot be assumed to be on the 
Directors’ machine(s).

# Info Files
The following files provide all the information regarding the competition. 
This includes:
- The Case Document
- Presentation
- Example Output
- GitHub Info

# Potentiall Useful Info:
We have given you all access to the images through OneDrive link here: 
https://dalu-my.sharepoint.com/:f:/r/personal/or942416_dal_ca/Documents/CEC_2025?csf=1&web=1&e=DNdeC3 

We suggest saving the folder via a zip file and then unzipping it locally to your computer. On average this method takes about 20min (assuming ~400KB/s). You can try syncing the OneDrive folder, however we find it takes longer to download the files that way.

## Retrieve Dataset
Below is an example code which accesseses this folder and then runs through using the root directory.

```ruby
import os
from os import path

dataset_dir = r"/Users/orionwiersma/Documents/CEC_2025"

# Initialize lists to hold data
image_paths = []
targets = []

total_images = 0

# Map for target labels
label_map = {'no':0,'yes':1}

for subdir in listdir(dataset_dir):
  subdir_path = path.join(dataset_dir, subdir)
  if path.isdir(subdir_path):
    subdir_path_list = listdir(subdir_path)
    for image in subdir_path_list:
      image_paths.append(path.join(subdir_path, image))
      targets.append(label_map[subdir])
    total_images += len(subdir_path_list)
    print(f"Number of images in '{subdir}' directory: {len(subdir_path_list)}")
print(f'Total number of images: {total_images}')
```
This should ouput something like this:
```
Number of images in 'no' directory: 9546
Number of images in 'yes' directory: 9828
Total number of images: 19374
```
## Checking File Paths
You may also want to check the file paths of your images:
```ruby
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'image_path': image_paths,
    'target': targets
}, index=np.arange(0, total_images))

print(df.head())
```
Which should output something like this:
```
                                          image_path  target
0  /Users/orionwiersma/Documents/augmented/no/no_...       0
1  /Users/orionwiersma/Documents/augmented/no/no_...       0
2  /Users/orionwiersma/Documents/augmented/no/no_...       0
3  /Users/orionwiersma/Documents/augmented/no/no_...       0
4  /Users/orionwiersma/Documents/augmented/no/no_...       0
```
