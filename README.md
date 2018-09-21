# Aimee Craig

[aimeecraig1@gmail.com](mailto:aimeecraig1@gmail.com)

I am a Junior Software Engineer Apprentice currently working for BGL Group.

## Notable Repositories

#### [Exchange Management Tool](https://github.com/aimeecraig/exchange-management-tool)
This initially began as a script for granting full access and send as permissions to mailboxes. I created the script below as granting these permissions using the Exchange Management Console GUI was time consuming, especially if a user required access to multiple mailboxes.

```powershell
Add-PSSnapin Microsoft.Exchange.Management.PowerShell.E2010 -ErrorAction SilentlyContinue
Clear-Host

function Show-Menu
{
    param (
        [string]$Title = "Select permission level:`n"
    )
    Clear-Host
    Write-Host "$Title"

    Write-Host "`t1: Full access only." -ForegroundColor Gray
    Write-Host "`t2: Full access and send as." -ForegroundColor Gray
    Write-Host "`n`tQ: Press 'Q' to quit." -ForegroundColor Red
}

do
{
    Show-Menu
    $input = Read-Host "`nPlease make a selection"
    switch ($input)
    {
        "1" {
            cls
            Write-Host "Full access only permission selected." -ForegroundColor Green
            # Apply full access perms #
            Add-MailboxPermission -Identity "$Mailbox" -User $Users -AccessRights FullAccess -InheritanceType All -WarningAction SilentlyContinue | Out-Null
            }

        "2" {
            cls
            # Apply full access perms #
            Add-MailboxPermission -Identity "$Mailbox" -User $Users -AccessRights FullAccess -InheritanceType All -WarningAction SilentlyContinue | Out-Null
            Write-Host -BackgroundColor DarkGreen -ForegroundColor White 'Full access perms added'

            # Apply send as perms #
            Get-User -Identity "$Mailbox" | Add-ADPermission -User "DOMAIN\$Users" -Extendedrights Send-As -InheritanceType All -WarningAction SilentlyContinue | Out-Null
            Write-Host -BackgroundColor DarkGreen -ForegroundColor White 'Send as perms added'
            "Full access and send as permission selected."
            }

        "q" {
            cls
            return
            }
    }
    pause
}
until ($input -eq 'q')

$Mailbox = Read-Host "Please enter the alias of the mailbox"
$Users = Read-Host "Please enter the username of the user/s (separate with comma)"
```

After using this particular script for a while, I created another script to view the permissions of a given mailbox. Then I created another, and another, and eventually decided to combine all of my Exchange scripts into one more user friendly tool. I also took the opportunity to refactor the code where I could but will continue this process on the repository here.

## Work Experience

#### Bauer Media (August 2015 to August 2018)    
*IT Service Desk Support Analyst*

- Self taught PowerShell in order to create a tool for myself and the other analysts to use in order to perform repeated Microsoft Exchange tasks.
- Providing first and second line support remotely and via telephone for various departments and divisions across the UK.
- Supporting Mac OS X and Windows systems, as well as various software packages including Adobe Creative Suite and Microsoft Office.
- Creating and updating user guides for use both internally and externally from the service desk.
- Troubleshooting and resolving the majority of calls at the first contact, and also working within agreed SLA targets.
- Supporting, along with a team of 7, over 3500 PCs and Macs across most of the UK.

#### Ideal Shopping Direct (March 2014 to August 2015)   
*Multi Skilled Studio Operator*

- Developing skills in camera operation; including positioning, framing, and movement.
- Working in a team of presenters, guests, directors, producers in order to establish technical requirements and look and feel for each show.
- Adjusting iris and colour controls during shows in order to produce a uniform output between cameras and keep standards within OFCOM guidelines.
- Lighting studio sets for each show, ensuring that products are clear of glare or otherwise unwanted artifacts.
- Video and audio patching of equipment.
- Editing music tracks to be used in live shows using Adobe Audition and selecting additional music to be used for individual events.

## Education

#### Makers Academy (September 2018 to present)

- Ruby
- RSpec

#### Birmingham City University (September 2010 to July 2013)

*Bachelor of Science in Film Production and Technology (Hons)*  
*Classification: 1st*

- 3DS Max and 3D computer graphics
- ADR, Foley and SFX dubbing
- Basic animation
- Camera operation
- Primary and secondary colour grading
- Editing video and audio
- Keyframing
- Lighting setup and operation
- On set sound mixing
- Photoshop and image design
- Previsualisation
- Rigging studio and location equipment
- Script writing and idea development
- Shot framing and composition
- Video, audio, and image compression
- Visual effects
