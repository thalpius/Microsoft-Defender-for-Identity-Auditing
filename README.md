> [!IMPORTANT]
> "This repo is now in 'Blue Screen' mode—archived and frozen in time!"

# Microsoft Defender for Identity Auditing

Microsoft Defender for Identity monitors your domain controllers by capturing and parsing network traffic and leveraging Windows events directly from your domain controllers. Auditing needs to be enabled for the Windows events to appear in the event viewer. Unfortunately, auditing is not on by default. Microsoft created a great docs page on configuring Windows event collection, but it is "a lot" of manual work, so I decided to make life a bit easier. I created an export of the policies needed for Microsoft Defender for Identity to enhance detection using the Windows events for others to import using a single command.

Microsoft docs describe five configurations. Ideally, all configurations need to be done for Microsoft Defender for Identity to enable enhanced detection. These are the five configuration settings.

1. Configure Audit Policies
2. Event ID 8004 (NTLM)
3. Event ID 1644 (Active Directory Web Service)
4. Configure Object Auditing
5. Auditing for Specific Detections (AD FS and Exchange)

For the first three configuration settings, I created a backup of a GPO, which you can import using a single command.

1. Download the files by clicking the green "Code" button on top of the repository, followed by "Download ZIP."
2. Unpack the files to a location you remember.
3. Run the PowerShell command shown below.

```PowerShell
Import-Gpo -BackupGpoName "Microsoft Defender for Identity Auditing" -TargetName "Microsoft Defender for Identity Auditing" -Path C:\UnpackedFiles -CreateIfNeeded
```

For more information see my blog post:

https://thalpius.com/2022/07/30/microsoft-defender-for-identity-auditing/
