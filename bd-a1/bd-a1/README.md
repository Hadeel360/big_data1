# BD-A1 Project

## Setup Instructions
1. Create Directory and insert bankloan dataset

2. Create Dockerfile

3. Create the Docker image:
   docker build -t bd-a1-image 
   
4. Run the Docker Container
docker run -it --name bd-a1-container bd-a1-image

5. Create Python Files
load.py to read dataset

dpre.py preprocessing data and save it in res_dpre.csv

eda.py generate 3 insights without visiualization and save them in text fils named eda-in-1.txt , eda-in-2.txt,eda-in-3.txt

vis.py creat visualization save it as vis.png


final.sh bash script to copy output files generated from python files from the container to local machine and to stop the container

6. Verify Outputs
ls -l
# My files
load.py
dpre.py
eda.py
vis.py
model.py

#Generated files
res_dpre.csv (Cleaned & transformed data)
eda-in-1.txt (EDA insight #1)
eda-in-2.txt (EDA insight #2)
eda-in-3.txt (EDA insight #3)
vis.png (Visualization)
k.txt (Cluster sizes from K-Mean

7. Create Bash Script
# Copy output files from container to local machine
docker cp bd-a1-container:/home/doc-bd-a1/res_dpre.csv bd-a1/service-result/
docker cp bd-a1-container:/home/doc-bd-a1/eda-in-1.txt bd-a1/service-result/
docker cp bd-a1-container:/home/doc-bd-a1/eda-in-2.txt bd-a1/service-result/
docker cp bd-a1-container:/home/doc-bd-a1/eda-in-3.txt bd-a1/service-result/
docker cp bd-a1-container:/home/doc-bd-a1/vis.png bd-a1/service-result/
docker cp bd-a1-container:/home/doc-bd-a1/k.txt bd-a1/service-result/

#Stop the container
docker stop bd-a1-container 

#Make the Bash Script Executable
chmod +x final.sh

#Run the Docker Container if I want to get back to container anytime
docker run -it --name bd-a1-container bd-a1-image 

8. Execute the Project
docker start -ai bd-a1-container
python3 load.py bankloan.csv
python3 dpre.py data.csv
python3 eda.py res_dpre.csv
python3 vis.py res_dpre.csv
python3 model.py res_dpre.csv
exit
./final.sh 

   
9. Pushing to Docker Hub & GitHub – Steps to push the Docker image and files. 
cd bd-a1/
git init
git add .
git commit -m "Final project files"
git branch -M main
git remote add origin https://github.com/Hadeel360/big_data1.git
git push -u origin main

