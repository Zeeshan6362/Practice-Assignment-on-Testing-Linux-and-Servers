# Practice-Assignment-on-Testing-Linux-and-Servers
Task 1:
sudo apt update
sudo apt install htop -y
<img width="1998" height="1708" alt="image" src="https://github.com/user-attachments/assets/93728419-0e2a-46f7-9311-6844913cebfe" />

htop
<img width="3274" height="2048" alt="image" src="https://github.com/user-attachments/assets/eaaa7f1d-a6f0-4465-88e5-a9efc0ff481b" />


df -h
sudo du -sh /var/log/*
<img width="3274" height="2048" alt="image" src="https://github.com/user-attachments/assets/3ba8a5ea-ecbe-4e23-95f4-566954350977" />


# Create a directory to store your reports
sudo mkdir -p /var/log/system_reports

# Write the disk space to a log file
echo "--- DISK SPACE ---" | sudo tee /var/log/system_reports/health_report.txt
df -h | sudo tee -a /var/log/system_reports/health_report.txt

# Append the current memory usage to the same file
echo -e "\n--- MEMORY USAGE ---" | sudo tee -a /var/log/system_reports/health_report.txt
free -m | sudo tee -a /var/log/system_reports/health_report.txt

<img width="2096" height="1734" alt="image" src="https://github.com/user-attachments/assets/fea7512d-7a79-4b91-896f-9e0d0904631a" />

Task 2:

sudo useradd -m Sarah
sudo useradd -m mike
sudo passwd Sarah
sudo passwd mike

<img width="1102" height="522" alt="image" src="https://github.com/user-attachments/assets/1da93673-7a0a-4b9e-a601-6b81b6fa9d52" />


sudo mkdir -p /home/Sarah/workspace
sudo mkdir -p /home/mike/workspace
# Hand over ownership
sudo chown -R Sarah:Sarah /home/Sarah/workspace
sudo chown -R mike:mike /home/mike/workspace

# Lock down the permissions
sudo chmod 700 /home/Sarah/workspace
sudo chmod 700 /home/mike/workspace

<img width="1480" height="540" alt="image" src="https://github.com/user-attachments/assets/280f6482-1a29-46d4-a7f3-efd4bc9e1ef2" />

sudo chage -M 30 Sarah
sudo chage -M 30 mike

sudo chage -l Sarah
<img width="1502" height="606" alt="image" src="https://github.com/user-attachments/assets/74ac3e59-ae45-4155-94f4-ca9b6eb9e837" />


sudo apt install libpam-pwquality -y
sudo bash -c 'echo "minlen = 12" >> /etc/security/pwquality.conf'
sudo bash -c 'echo "ucredit = -1" >> /etc/security/pwquality.conf'
sudo bash -c 'echo "dcredit = -1" >> /etc/security/pwquality.conf'

<img width="3274" height="2048" alt="image" src="https://github.com/user-attachments/assets/87fab748-e947-47bb-a1b5-202f1b008a7d" />



Task 3: 
sudo mkdir -p /etc/httpd /var/www/html /etc/nginx /usr/share/nginx/html /backups
sudo touch /etc/httpd/httpd.conf /var/www/html/index.html /etc/nginx/nginx.conf /usr/share/nginx/html/index.html
# Create Sarah's Apache backup script
echo 'tar -czf /backups/apache_backup_$(date +%F).tar.gz /etc/httpd /var/www/html' | sudo tee /home/Sarah/backup.sh
# Create Mike's Nginx backup script
echo 'tar -czf /backups/nginx_backup_$(date +%F).tar.gz /etc/nginx /usr/share/nginx/html' | sudo tee /home/mike/backup.sh
# Make both scripts executable
sudo chmod +x /home/Sarah/backup.sh /home/mike/backup.sh
sudo /home/Sarah/backup.sh
sudo /home/mike/backup.sh
ls -l /backups/

<img width="3274" height="2048" alt="image" src="https://github.com/user-attachments/assets/3ca39e12-f18f-48d6-a156-c5949501e7e3" />



#Note to the evaluator: These assessments are above our knowledge of expertise and whatever is being taught in the classes. Concepts that are needed to complete these practise assessments are never covered in the Live classes neither we have any notes for reference. I had to rely on copilot to complete this high level assessment. I do not like doing these assessments just for the sake of doing. Humble request to the assessment creator -- kindly look in to our skill sets we have and also the topics that are covered in the live sessions -- and plan the assessments accordingly. I know these assessments are great to get idea and experience about what we should be knowning -- but without learning/teaching these topics and trying to work on assignments feels like working blindly without anything making sense to us. 



















