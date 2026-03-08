# peft-boft-dreambooth-toy-goose

Parameter-efficient fine-tuning of Stable Diffusion v1.5 using BOFT (Butterfly Orthogonal Fine-Tuning) for subject-driven generation



\## Overview

Fine-tuned `runwayml/stable-diffusion-v1-5` using \*\*Butterfly Orthogonal Fine-Tuning (BOFT)\*\* from Hugging Face PEFT for subject-driven image generation.



\- Subject: Toy goose (white fur + red scarf)

\- Trainable parameters: 11.75M (1.35% of total)

\- Training steps: 610



\## Repository Structure

peft-boft-dreambooth-toy-goose/

├── train\_dreambooth.py

├── train\_dreambooth\_windows.sh     # Windows version

├── requirements.txt

├── dreambooth\_inference.ipynb

├── loss\_curve.png

└── README.md



\## How to Reproduce (Windows 11)



```bash

\# 1. Clone this repo

git clone https://github.com/YOUR-USERNAME/peft-boft-dreambooth-toy-goose.git

cd peft-boft-dreambooth-toy-goose



\# 2. Create conda environment

conda create -n peft python=3.10

conda activate peft



\# 3. Install requirements

pip install -r requirements.txt



\# 4. Run training (Windows fix included)

accelerate launch train\_dreambooth.py ^

&nbsp; --pretrained\_model\_name\_or\_path="runwayml/stable-diffusion-v1-5" ^

&nbsp; --instance\_data\_dir="./data/dreambooth/dataset/goose\_toy" ^

&nbsp; --class\_data\_dir="./data/class\_data/goose\_toy" ^

&nbsp; --output\_dir="./data/output/boft" ^

&nbsp; --wandb\_project\_name="dreambooth\_boft" ^

&nbsp; --wandb\_run\_name="goose\_toy\_1\_boft\_80" ^

&nbsp; --with\_prior\_preservation --prior\_loss\_weight=1.0 ^

&nbsp; --instance\_prompt="a photo of a cms goose" ^

&nbsp; --class\_prompt="a photo of goose" ^

&nbsp; --validation\_prompt="a photo of a cms goose in the jungle. a photo of a cms goose in the snow. a photo of a cms goose on the beach." ^

&nbsp; --resolution=512 ^

&nbsp; --train\_batch\_size=2 ^

&nbsp; --num\_dataloader\_workers=0 ^

&nbsp; --lr\_scheduler="constant" ^

&nbsp; --lr\_warmup\_steps=0 ^

&nbsp; --num\_class\_images=200 ^

&nbsp; --use\_boft ^

&nbsp; --boft\_block\_num=8 ^

&nbsp; --boft\_block\_size=0 ^

&nbsp; --boft\_n\_butterfly\_factor=1 ^

&nbsp; --boft\_dropout=0.1 ^

&nbsp; --boft\_bias="none" ^

&nbsp; --learning\_rate=3e-5 ^

&nbsp; --max\_train\_steps=610 ^

&nbsp; --checkpointing\_steps=150 ^

&nbsp; --validation\_steps=150 ^

&nbsp; --report\_to="wandb"

