VMware/host issue
-----

### Step 1: Check "Connected" checkbox in VMware (most likely fix)

1. In VMware, shut down the Kali VM (not suspend — fully power off)
2. Right-click the Kali VM tab → Settings
3. Select Network Adapter
4. Ensure both are checked:
5. ✅ Connected
6. ✅ Connect at power on
7. Click OK
8. Power on the VM again
9. Run ip a in Kali

-----

### Step 2: If still not working — reset VMware virtual network on Windows

1. On your Windows host (not in the VM):
2. Open VMware Workstation
3. Click Edit → Virtual Network Editor

<img width="461" height="295" alt="Screenshot 2026-05-04 112240" src="https://github.com/user-attachments/assets/16cdd76d-7170-47a9-8825-532367a7eed3" />

4. Click Change Settings (bottom right — needs admin)

<img width="849" height="717" alt="Screenshot 2026-05-04 112349" src="https://github.com/user-attachments/assets/00dfdd45-03d4-4c18-bcaf-63cbbf474f83" />

5. Select VMnet8 (NAT)
6. Click Restore Defaults (bottom left)

<img width="209" height="59" alt="Screenshot 2026-05-04 112401" src="https://github.com/user-attachments/assets/cc8cacd6-afdf-4f9c-ab1d-76558dcc6a76" />

7. Wait for it to complete
8. Click Apply → OK

<img width="635" height="776" alt="Screenshot 2026-05-04 112429" src="https://github.com/user-attachments/assets/818bf1ea-a56a-42d1-a256-0d04423017f0" />

9. Restart your Kali VM

----

### Step 3: If still NO-CARRIER — remove and re-add the network adapter

1. Shut down Kali VM
2. Go to Edit Settings
3. Select Network Adapter
4. Click Remove
5. Click Add → Network Adapter → Finish
6. Set it to NAT
7. Ensure Connected and Connect at power on are checked
8. Start the VM

