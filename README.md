INC0012871 - Replacing a Dead Customer Support Desktop

This is a write-up of how I handled a Critical ticket in the ServiceDesk Simulator: a Customer Support agent's desktop completely died, so I built a replacement from the imaging server and shipped it out.

The ticket

Quinn Adams from Customer Support (Floor 1, x2280) reported that their desktop would not turn on at all. No lights, no fan, no beep. They had already tried the power button a few times and checked the wall outlet with another device, which worked. Calls were queueing up and nobody could take them, so the ticket was marked Critical.

<img src="images/01-ticket-queue.png" width="800"> <img src="images/02-ticket-details.png" width="800">

Since the outlet was fine and the machine showed no sign of life, I decided the quickest fix was to build a replacement desktop and ship it with a return label for the faulty one.

Step 1: Read the SOP

Before touching anything I read the Deployment SOP (SOP-OSD-014). It has the deployment account, the first-login password and the computer naming convention, so it saves you from guessing later.

<img src="images/03-sop-start.png" width="800">
Step 2: Pick the workstation

I chose Desktop Deployment and hit Start setup.

<img src="images/04-choose-desktop.png" width="800">
Step 3: Connect the cables

I connected all 5 cables on the rear panel: power, ethernet, DisplayPort, USB keyboard and USB mouse. Once everything showed as connected I clicked Boot.

<img src="images/05-physical-setup.png" width="800">
Step 4: Catch the boot menu

I missed the boot menu on my first try and the OS just started normally, so I had to restart. The second time I pressed F12 repeatedly during POST and got in.

<img src="images/06-boot-menu-missed.png" width="800"> <img src="images/07-press-f12.png" width="800">
Step 5: Boot from the network

In Boot Manager I picked the PXE network boot option so the machine would image from the deployment server instead of the internal SSD.

<img src="images/08-boot-manager.png" width="800">
Step 6: Deployment share password

The wizard asks for the task sequence password. I took it from the SOP and clicked Next.

<img src="images/09-task-sequence-password.png" width="800"> <img src="images/10-password-entered.png" width="800">
Step 8: Name the computer

The Task Sequence Wizard asks you to set the OSDCOMPUTERNAME variable. I didn't want to guess the name, so I checked the SOP. Every machine is called SD followed by four digits, and that value is also the asset tag. I went with SD1341.

<img src="images/11-variables-empty.png" width="800"> <img src="images/12-edit-variable.png" width="800"> <img src="images/13-sop-naming-convention.png" width="800"> <img src="images/14-name-entered.png" width="800"> <img src="images/15-name-set.png" width="800">
Step 11: Sign in to verify the build

The last step is a single domain sign-in to confirm the build worked. The SOP says to use your display name and the shared domain password. The domain join itself is automatic, so there is no join password to enter.

<img src="images/16-domain-signin.png" width="800"> <img src="images/17-credentials-entered.png" width="800">

The deployment finished successfully.

<img src="images/18-deployment-successful.png" width="800">
Step 12: PC Shelf

SD1341 showed up on the PC Shelf as ready to ship, so I opened Ship Manager.

<img src="images/19-pc-shelf.png" width="800">
Step 13: Get the delivery address

Ship Manager needs a street address and I didn't have one, so I messaged Quinn in Company Chat and asked for the receiving dock address.

<img src="images/20-ship-manager-empty.png" width="800"> <img src="images/22-company-chat-list.png" width="800"> <img src="images/23-quinn-address.png" width="800">

Quinn replied with:

1200 Commerce Park Drive
Columbus, OH 43215
Step 14: Ship it

Settings I used in Ship Manager:

Recipient: Quinn Adams
Sender: IT Department
Computer: SD1341
Shipping speed: Rush Priority (Instant)
Include return label: ticked, returning to IT Department (1 Helpdesk Way, Denver, CO 80202)
<img src="images/21-ship-options.png" width="800"> <img src="images/24-ship-form-filled.png" width="800"> <img src="images/25-return-and-ship.png" width="800">
Step 15: Close the ticket

Last thing was closing the ticket with a resolution note so whoever looks at it next knows what happened. The ticket moved to Recently closed as Resolved and I got 34 points.

<img src="images/26-close-ticket.png" width="800"> <img src="images/27-ticket-resolved.png" width="800">

Short version of the note:

Original desktop confirmed non-functional (no power, outlet verified working). Replacement desktop SD1341 built via OSD per SOP-OSD-014 and verified with domain sign-in. Shipped to Quinn Adams at the receiving dock via Rush Priority with a return label for the faulty unit. Ticket resolved.
What I learned
Read the SOP first. The naming convention and passwords are all in there.
If you miss the F12 boot menu, just restart and try again.
The computer name is also the asset tag, so use the SD#### format.
Always get the delivery address from the user before shipping.
Add a return label so the broken hardware comes back.
Write a proper resolution note.
