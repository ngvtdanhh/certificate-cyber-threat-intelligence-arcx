# 🔍 YARA Rule Writing Demo

This demo shows how to detect a known malware family using custom YARA rules.

---

## 🎯 Objective

Detect binaries exhibiting traits of a keylogger using string and hex signatures.

---

## 📄 Sample YARA Rule

```yara
rule keylogger_malware
{
    meta:
        description = "Detects basic keylogger strings"
        author = "Thành Danh"
        threat_group = "Unknown"

    strings:
        $s1 = "GetAsyncKeyState"
        $s2 = "User32.dll"
        $s3 = "CreateFileA"
    
    condition:
        all of them
}
```

## ⚙️ Test with CLI

```bash
yara keylogger_malware.yar suspicious.exe
```

## Output
```nginx
keylogger_malware suspicious.exe
```
## 🔐 Pro Tip

Combine string signatures with file size, entrypoint offsets, or PE section entropy
