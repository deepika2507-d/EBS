# EBS
EBS -

WORKING WITH EBS

NAME: DEEPIKA V

REG NO: 212224240030

Aim

To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.


Algorithm / Steps

1.Create a new Amazon EBS volume with a size of 1 GiB.
2.Select the same Availability Zone as the EC2 instance.
3.Attach the EBS volume to the EC2 instance using /dev/sdb.
4.Connect to the EC2 instance using AWS Systems Manager Session Manager.
5.Check the available storage using df -h.
6.Create an ext3 file system on the EBS volume.
7.Create the /mnt/data-store directory.
8.Mount the EBS volume to /mnt/data-store.
9.Configure /etc/fstab for automatic mounting.
10.Verify that the EBS volume is successfully mounted.
11.Create file.txt inside the mounted EBS volume.
12.Verify the contents of the created file.
13.Create an EBS snapshot named My Snapshot.
14.Delete file.txt from the original EBS volume.
15.Create a new EBS volume from the snapshot.
16.Attach the restored volume to the EC2 instance using /dev/sdc.
17.Create the /mnt/data-store2 directory.
18.Mount the restored volume to /mnt/data-store2.
19.Verify that file.txt has been successfully restored.

Program
1. Check Available Storage
```
df -h
```
3. Create an ext3 File System
```
sudo mkfs -t ext3 /dev/sdb
```
4. Create a Mount Directory
```
sudo mkdir /mnt/data-store
```
4. Mount the EBS Volume
```
sudo mount /dev/sdb /mnt/data-store
```
6. Configure Automatic Mounting
```
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```
7. View the File System Configuration
```
cat /etc/fstab
```
8. Verify the Mounted Volume
```
df -h
```
9. Create a File in the EBS Volume
```
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```
10. Read the File
```
cat /mnt/data-store/file.txt
```
11. Delete the File
```
sudo rm /mnt/data-store/file.txt
```
12. Verify File Deletion
```
ls /mnt/data-store/
```
13. Create a Mount Directory for the Restored Volume
```
sudo mkdir /mnt/data-store2
```
14. Mount the Restored EBS Volume
```
sudo mount /dev/sdc /mnt/data-store2
```
15. Verify Snapshot Restoration
```
ls /mnt/data-store2/
```
Expected output:
```
file.txt
```
Outputs


<img width="1097" height="627" alt="image" src="https://github.com/user-attachments/assets/062e1060-fa49-4893-96c1-01654c091ebd" />


<img width="855" height="589" alt="image" src="https://github.com/user-attachments/assets/e01a2bda-4f3c-45ae-aa27-a6614a57024c" />


<img width="1209" height="291" alt="image" src="https://github.com/user-attachments/assets/3bf5f034-348c-4f82-bbf4-ac442d29466f" />


<img width="1216" height="190" alt="image" src="https://github.com/user-attachments/assets/d1835d5f-7368-45b4-b7c6-f1ce519465c5" />


<img width="1207" height="650" alt="image" src="https://github.com/user-attachments/assets/59cefab1-c400-4d88-ba62-3f310235360e" />

Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
