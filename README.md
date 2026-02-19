**Windows Registry Editor Version 5.00**

Here is the standardized `.reg` (Registry) file content, ready for you to copy and use. I have used the `%LocalAppData%` environment variable so this file will work on any computer without needing to manually edit your username.

### Step 1: Create the Registry File

Copy the code below, paste it into **Notepad**, and save it as `fix_vscode.reg`.

```reg
Windows Registry Editor Version 5.00

; --- Add to the menu when right-clicking on a FOLDER ---
[HKEY_CLASSES_ROOT\Directory\shell\vscode]
@="Open with Code"
"Icon"="%LocalAppData%\\Programs\\Microsoft VS Code\\Code.exe"

[HKEY_CLASSES_ROOT\Directory\shell\vscode\command]
@="\"%LocalAppData%\\Programs\\Microsoft VS Code\\Code.exe\" \"%1\""

; --- Add to the menu when right-clicking on the BACKGROUND inside a folder ---
[HKEY_CLASSES_ROOT\Directory\Background\shell\vscode]
@="Open with Code"
"Icon"="%LocalAppData%\\Programs\\Microsoft VS Code\\Code.exe"

[HKEY_CLASSES_ROOT\Directory\Background\shell\vscode\command]
@="\"%LocalAppData%\\Programs\\Microsoft VS Code\\Code.exe\" \"%V\""

; --- Add to the menu when right-clicking on a FILE ---
[HKEY_CLASSES_ROOT\*\shell\OpenWithVSCode]
@="Open with Code"
"Icon"="%LocalAppData%\\Programs\\Microsoft VS Code\\Code.exe"

[HKEY_CLASSES_ROOT\*\shell\OpenWithVSCode\command]
@="\"%LocalAppData%\\Programs\\Microsoft VS Code\\Code.exe\" \"%1\""

```

---

### Step 2: Activation

1. **Save the file**: Press `Ctrl + S`, set "Save as type" to **All Files (*.*)**, and name it `install_vscode_menu.reg`.
2. **Run the file**: Double-click the file you just created.
3. **Confirm**: A prompt will appear asking if you want to continue. Click **Yes**.
4. **Verify**: Right-click any folder or file to see the results.

---

### ⚠️ Important Notes:

The code above is designed for the **User Setup** version of VS Code (Microsoft's default).

* If you installed the **System Setup** version (usually located in `C:\Program Files`), replace all instances of `%LocalAppData%\\Programs\\Microsoft VS Code` with `C:\\Program Files\\Microsoft VS Code`.
* On **Windows 11**, the option might still be tucked away under **"Show more options"** (or press `Shift + Right Click`) unless you have disabled the new simplified context menu.
