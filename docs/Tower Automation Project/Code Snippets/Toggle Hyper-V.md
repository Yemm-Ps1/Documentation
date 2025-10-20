LDPlayer conflicts with Hyper-V, and it needs to be disabled.

```
:: Disable Hyper-V (for LDPlayer)
bcdedit /set hypervisorlaunchtype off
shutdown /r /t 0

:: Enable Hyper-V again (for WSL/Docker)
bcdedit /set hypervisorlaunchtype auto
shutdown /r /t 0

```

