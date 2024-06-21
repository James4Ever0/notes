---
title: migrate conda installation folder
created: '2024-06-21T01:20:21.771Z'
modified: '2024-06-21T01:23:12.202Z'
---

# migrate conda installation folder

To copy the entire Conda user data directory to another disk and then create a symbolic link back to the original place, you can follow these steps:

Identify the Conda user data directory: This is typically located at `~/.conda` or `~/miniconda3` or `~/anaconda3`, depending on how you installed Conda. You can find the exact path by running `conda info --envs` and looking for the envs dirs entry.

Copy the directory to the new location: Use rsync to copy the directory, as it will preserve the file permissions and symbolic links. Here's an example command:

```bash
rsync -avh --progress ~/.conda /path/to/new/location/conda_data_backup
```

Replace `/path/to/new/location/conda_data_backup` with the actual path where you want to copy the directory on the other disk.

Create a symbolic link: Once the copy is complete, you can create a symbolic link from the original location to the new one. First, you may need to remove the original directory or move it to a different name. Here's how you can do it:

```bash
mv ~/.conda ~/.conda_old  # Rename the original directory
ln -s /path/to/new/location/conda_data_backup ~/.conda  # Create the symlink
```

Make sure to replace `~/.conda` with the actual path to your Conda user data directory and `/path/to/new/location/conda_data_backup` with the path to the copied directory on the new disk.

Test the setup: Before deleting the old directory, test your new setup to ensure everything is working correctly. Activate your Conda environments and run some commands to verify that packages are accessible and that you can install new ones.

Clean up: If everything works as expected, you can now delete the old directory:

```bash
rm -rf ~/.conda_old
```

Update Conda's configuration: Conda may have configuration files that reference the old directory. You should update these to reflect the new location. You can find Conda configuration files in `~/.condarc` or `~/condarc` and in the Conda environment directories themselves.

Verify the symlinks within the directory: If there are relative symlinks within the Conda user data directory that are now broken due to the move, you will need to fix them. You can use the find command to locate broken symlinks:

```bash
find /path/to/new/location/conda_data_backup -type l -ls | grep ' No such file or directory'
```

Then, you can either manually fix these symlinks or use a script to update their paths accordingly.

By following these steps, you should be able to move your Conda user data directory to another disk and create a symbolic link back to the original location without losing any functionality. Remember to back up your data before making any changes, and ensure that you have the necessary permissions to create symbolic links and write to the new location.
