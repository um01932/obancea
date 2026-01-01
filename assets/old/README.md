This folder is intended to contain the original PNG/JPG/JPEG image files after migrating the site to use WebP images.

I couldn't move binary files automatically from the repository. To move your existing PNG/JPG/JPEG assets into this folder locally, run one of the commands below in PowerShell from the project root.

# Move all PNG/JPG/JPEG files from assets into assets/old (PowerShell)
# This moves files and overwrites if target exists. Adjust as needed.
Get-ChildItem -Path .\src\assets -Include *.png,*.jpg,*.jpeg,*.JPG,*.PNG,*.JPEG -File | ForEach-Object { Move-Item -Path $_.FullName -Destination .\src\assets\old\ -Force }

# Or using cmd (Windows):
:: move *.png src\assets\old
:: move *.jpg src\assets\old

# After moving, verify the site still loads WebP images and commit changes.
