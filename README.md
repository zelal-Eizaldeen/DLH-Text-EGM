# DLH-Project-Text-EGM
# Create a virtual environment named 'envname' with 
 python3 -m venv venv
 or
 python -m venv venv

# Activate the environment # On macOS/Linux: 
source venv/bin/activate
or 
on Windows: venv\Scripts\activate

# Upgrade pip (optional but recommended) 
pip install --upgrade pip

# Added those tlibraries to requirements.txt
pyts
wfdb

# For mac: 
curl -O https://physionet.org/static/published-projects/iafdb/intracardiac-atrial-fibrillation-database-1.0.0.zip
Instead of
wget https://physionet.org/static/published-projects/iafdb/intracardiac-atrial-fibrillation-database-1.0.0.zip


# ON windows:
curl -o iafdb.zip https://physionet.org/static/published-projects/iafdb/intracardiac-atrial-fibrillation-database-1.0.0.zip

# To run sh preprocess.sh without error, problem solved by adding .path to read_all(arg.path) inside preprocess_intra.py
egm_signals = read_all(args.path)

# Change the train_ecg into train.py inside train.sh file
python train.py --device=cuda:0 --batch=4 --patience=5 --model=big --mask=0.75 --use_ce

# Add norm_loss into train.py
parser.add_argument('--norm_loss', type=float, default=1.0, help='Please choose the normalization loss weight')

# CUDA Problem on iMac: 
If you have an Apple Silicon (M1/M2/M3) or AMD GPU → You CANNOT use CUDA.
How to check?
in terminal execute the following command:
system_profiler SPDisplaysDataType

Look for the "Chipset Model" or "Graphics" section.
If you see AMD or Apple Silicon (M1/M2/M3) → CUDA is NOT supported
- If CUDA is not supported, you should use PyTorch's Metal backend for acceleration instead:
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
# Check if Metal is enabled
-import torch
print(torch.backends.mps.is_available())  


# Run inference.sh using cpu
1- remove the cuda from inference.sh 
- 3-python inference.py --device=cpu --batch=1 --checkpoint='saved_2' --model=big --inference --mask=0.75
2- Execute the following command
- sh inference.sh --checkpoint runs/checkpoint/saved_2/best_checkpoint.chkpt



