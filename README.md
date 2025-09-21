This file is just using all the tools available. The bigger thing is to download the flickr8k package from Kaggle and Python packages like transformer, pytorch, torchvision, torchaudio.
It build captions from BLIP captioning tool from salesforce. In order make this model, you need to follow these steps:
Step-1: Setup: copy the following code in your command prompt to create a "vlm_env" which is different from kernel environment
python -m venv vlm_env
vlm_env\Scripts\activate
Installing of Dependencies
Run each line one by one:
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install transformers datasets accelerate peft pillow open_clip_torch

python train_captioning.py
After this point, it will take some time to download, so don't worry. Your last message should be:
Successfully installed torch torchvision torchaudio pillow numpy ...

Step-2: Installation of Flickr8k
Install Kaggle API (needed to download Flickr8k):
pip install kaggle

Set up Kaggle credentials
Go to https://www.kaggle.com
 → log in.
Click on your profile picture → Account.
Scroll to API → click Create New API Token.
This will download a file: kaggle.json.
Move it to this path on your system:
C:\Users\<your-username>\.kaggle\kaggle.json

(replace <your-username> with your Windows username, probably admin in your case).

Download Flickr8k
Run this command in Anaconda prompt:
kaggle datasets download -d adityajn105/flickr8k
This will give you a zip file flickr8k.zip.

Unzip the dataset
unzip flickr8k.zip -d flickr8k

Once done, run this quick test to confirm Kaggle API is working:
kaggle datasets list -s flickr8k

Verify Dataset
You can quickly check inside Python:
import pandas as pd
df = pd.read_csv("flickr8k/captions.txt")
print(df.head())
