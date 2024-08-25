## <ins>**Installing Windows with an Answer File**</ins>
In short, you need to include the `autounattend.xml` answer file on your Windows Installation Media so it can be read and executed during the Windows Setup. Here are a few ways to do it:

> [!NOTE]<br/>
> - The filename included on the root of the Windows Installation Media must be `autounattend.xml` or else it won't execute.
<br/>

### <ins>Method 1: Create a Bootable Windows Installation Media</ins>

1. Download your preferred `autounattend.xml` file and save it on your computer.
2. Create a [Windows 10](https://www.microsoft.com/en-us/software-download/windows10) or [Windows 11](https://www.microsoft.com/en-us/software-download/windows11) Bootable Installation USB drive with [Rufus](https://rufus.ie/en/) or the Media Creation Tool. 
> [!IMPORTANT]<br/>
> - Some users have reported issues with the Media Creation Tool when creating the Windows Installation USB. Use it at your own discretion. <br/>
> - When using Rufus, don’t select any of the checkboxes in “Customize Your Windows Experience” as it creates another `autounattend.xml` file that might overwrite settings in the UnattendedWinstall file.
3. Copy the `autounattend.xml` file you downloaded in Step 1 to the root of the Bootable Windows Installation USB you created in Step 2.
4. Boot from the Windows Installation USB, do a clean install of Windows as normal, and the scripts will run automatically.
</br>

### <ins>Method 2: Create a Custom ISO File</ins>

1. Download your preferred `autounattend.xml` file and save it on your computer.
2. Download the [Windows 10](https://www.microsoft.com/en-us/software-download/windows10) or [Windows 11](https://www.microsoft.com/en-us/software-download/windows11) ISO file depending on the version you want.
3. Download and Install [AnyBurn](https://anyburn.com/download.php)
   - In AnyBurn, select the “Edit Image File” option.
   - Navigate to and select the Official Windows ISO file you downloaded in Step 2.
   - Click on “Add” and select the `autounattend.xml` file you downloaded in Step 1 or just click and drag the `autounattend.xml` into the AnyBurn window.
   - Click on “Next,” then on “Create Now.” You should be prompted to overwrite the ISO file, click on “Yes.”
   - Once the process is complete, close AnyBurn.
4. Use the ISO file to Install Windows on a Virtual Machine OR use a program like [Rufus](https://rufus.ie/en/) or [Ventoy](https://github.com/ventoy/Ventoy) to create a bootable USB flash drive with the edited Windows ISO file.
> [!IMPORTANT]<br/>
> - When using Rufus, don’t select any of the checkboxes in “Customize Your Windows Experience” as it creates another `autounattend.xml` file that might overwrite settings in the UnattendedWinstall file.
5. Boot from the Windows Installation USB, do a clean install of Windows as normal, and the scripts will run automatically.
</br>

### <ins>Method 3: Use Ventoy Auto Install Plugin</ins>

1. Download your preferred `autounattend.xml` file and save it on your computer.
2. Download the [Windows 10](https://www.microsoft.com/en-us/software-download/windows10) or [Windows 11](https://www.microsoft.com/en-us/software-download/windows11) ISO file, depending on the version you want.
3. Download and install [Ventoy](https://github.com/ventoy/Ventoy) to your desired USB flash drive. 
4. Prepare the folder structure:
    - In your newly created Ventoy USB disk, create the following folders: `ISO` and `Templates`. <br/> *They should be at the root of the drive.*
    - Inside of the `ISO` folder, create a new folder called `Windows`.
    - Copy your Windows ISO files in the `ISO\Windows` folder.
    - Copy your `autounattend.xml` into the `Templates` folder.
5. Start VentoyPlugson. Depending on your OS, the steps might differ.
    - On Windows, run the `VentoyPlugson.exe` file.
    - A new browser window should open up with a Ventoy web interface ready to go.
    - Select the `Auto Install Plugin` menu from the list.
    - Click on the `Add` button.
    - Select [parent] to make the whole Windows ISO folder benefit from the plugin.
    - In the Directory Path, paste in the absolute path to your `Windows` folder. </br> example: `F:\ISO\Windows` (Replace `F` with your drive letter.)
    - In the Template Path, paste in the absolute path to your `autounattend.xml` file. </br> example: `F:\Templates\autounattend.xml` (Replace `F` with your drive letter.) <br/> (PSA: If you have more `autounattend.xml` files, you can add them later on!)
    - Click on `OK` and you should see a message saying that the configuration has been saved successfully.
    - Close the VentoyPlugson browser window and stop the VentoyPlugson application.
6. Boot from the Ventoy USB drive in the computer where you want to install windows.
   - After selecting a Windows ISO to boot from, you will be prompted to boot with the `/Templates/autounattend.xml` file.
   - Select that option and the `autounattend.xml` will be automatically executed during installation.
</br>
