# FilesBackupTool
Actually the original project has name a FlexibleBackupTool. This tool has been developed to backup huge amount of files from different network places. It is helping to collect necessary type of data in particular place and mark the bundle by the timestamp. In the settings for the gathering of the files you may choose to delete the source files or leave it in the same place. 
In the settings for particular type of folder you may backup only that file that has been modified from the last time of backup. In this situation the backup archive will be separated by the time stamp and consist of the only modified files. If you need to find the  previous version of file you look at the older timestamp of archive in the folder of backups.

This tool is implemented in production where the measurement log files gathering from the machines on the several lines. The type of files has different mime types: text, image. The machines generates big amount of files in hour. In this case the settings adjusted to the deletes of source files that incoming to backup but the new files from the machine in the same folder will stay on the place and go to the backup on the next itteration.

In the production uses programs to the measures and in this case the setting options works to backup only the modifies programs without deletes from the folder.

# Requirements
To run an executable <a href="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/target">`jar`</a> file the OS have to have Java jdk 1.7 or higher version.

# How to run java application?
The executable <a href="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/target">`jar`</a> file has several attributes:

| Attribute name | Syntax | Description |
| -------------- | ----------------------- | ----------------------- |
| workspace | workspace=/path/to/workspace/directory/ | mandatory attribute |
| tempdir | temdir=/path/to/other/logic/drive/ | optional (local drive only) |
| restore | restore | this is works only if the tag checksum is on TRUE in the settings.xml |

To the correct running of the script mandatory have to have in the directory of workspace two files: settings.xml; log4j.properties;
That files are located in the folder <a href="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/backup-workspace">backup-workspace</a>.

The <a href="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/backup-workspace/settings.xml">**settings.xml**</a> well documented file and you need to change parameters for your needs.
About <a href="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/backup-workspace/log4j.properties">**log4j.properties**</a> read more from the http://logging.apache.org/log4j/1.2/manual.html if you need to customize log output.

# In practice
In practice the better way is to keep executable jar file in the separate place from the workspaces.
An each workspace consist of the settings.xml with individual options and log4j.properties file in the one folder. The other files will creates by the application if is not exists.
The best practice to use application is to create bash script for each workspace in any comfortable folder.
## Linux bash example
```bash
#!/bin/bash
jar_file_path="/home/user/backupjar/FlexibleBackupTool-2.1.9-shaded.jar"
workspace_path="/home/user/workspace/" 
temp_path="/var/shared/tmp/"
java -jar $jar_file_path workspace=$workspace_path tempdir=$temp_path
```
## Windows bash example
```bash
@echo off
SET jar_file_path=C:\Users\tn_gordm\Devspaces\eclipse-workspace\FlexibleBackupTool-2.1.9\target\FlexibleBackupTool-2.1.9-shaded.jar
java -jar workspace=C:\Users\tn_gordm\Devspaces\eclipse-workspace\FlexibleBackupTool-2.1.9\backup-workspace\ tempdir=D:\temp\
timeout 30
```
# Script illustration
## Gathering checksum of file
When everything start with no errors you will see something similar in your terminal:
<p align="center">
  <img src="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/img_examples/checksum-example.jpg" width="640" title="file checksum">
</p>

## Archiving file
<p align="center">
  <img src="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/img_examples/archive-example.jpg" width="640" title="file archive">
</p>

## At the end
<p align="center">
  <img src="https://github.com/inc0d3w3trust/FilesBackupTool/blob/main/img_examples/finish-example.jpg" width="640" title="the end of backup">
</p>
As an example of the illustration above has presented <a href="https://github.com/inc0d3w3trust/FilesBackupTool/tree/main/backup-workspace" target="_blank">backup-workspace</a> folder with the results of the script.
