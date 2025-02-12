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

