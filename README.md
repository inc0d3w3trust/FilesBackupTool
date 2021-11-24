# FilesBackupTool
Actually the original project has name a FlexibleBackupTool. This tool has been developed to backup huge amount of files from different network places. It is helping to collect necessary type of data in particular place and mark the bundle by the timestamp. In the settings for the gathering of the files you may choose to delete the source files or leave it in the same place. 
In the settings for particular type of folder you may backup only that file that has been modified from the last time of backup. In this situation the backup archive will be separated by the time stamp and consist of the only modified files. If you need to find the  previous version of file you look at the older timestamp of archive in the folder of backups.

This tool is implemented in production where the measurement log files gathering from the machines on the several lines. The type of files has different mime types: text, image. The machines generates big amount of files in hour. In this case the settings adjusted to the deletes of source files that incoming to backup but the new files from the machine in the same folder will stay on the place and go to the backup on the next itteration.

In the production uses programs to the measures and in this case the setting options works to backup only the modifies programs without deletes from the folder.

# Requirements
To run an executable `jar` file the OS have to have Java jdk 1.7 or higher version.

# How to run java application?
The executable 'jar' file has several attributes. 
The the main and permanent attribute - `workspace=/path/to/appication/settings/and/log/property/files/`.
Optional attribute - `tempdir=/path/to/other/logic/drive/with/exdended/memory/`. By default application uses temporary folder of the OS to create the ZIP archive before the move it to the path from settings.xml. **NB! DO NOT USE MAPPED DRIVES FOR tempdir** - this is not works for the application, local drive only.
To restore fresh files from the backups uses attribute - `restore`. All files will be restored to the predefined directory in settings.xml.

# In practice
In practice the better way is to place executable jar file in the separate place from the workspaces. 
An each workspace consist of the settings.xml with individual options and log4j.properties file in the one folder. The other files will creates by the application if is not exists.
