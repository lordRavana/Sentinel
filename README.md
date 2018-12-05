# PrimeStone Sentinel

*You only need this if you are running a masternode and getting WATCHDOG_EXPIRED*

Please test it and consider it to be a **beta**, something might fail (I don't have primestone in Windows).

Pick an executable (either win/lin) from https://github.com/Primestonecoin/Sentinel
Just for reference, sentinel-win64 virustotal (3/67): https://www.virustotal.com/es/file/3a65c0df1fb89607531d8c02bb2a3070f1c39f555944d118c67d8ee616be5b18/analysis/1510697796/

Use at your own risk, it has been compiled exactly as the Github repo says

## Before running it

**1.** Make sure you are running v1.1.0

**2.** Close your wallet

**3.** Go to primestonecore folder and delete "mncache.dat" and "mnpayments.dat"

**4.** Make sure your "primestone.conf" contains, at least, the following data:
rpcuser=myrpcuser
rpcpassword=myrpcpass
server=1
rpcport=19984
rpcconnect=127.0.0.1

Try to make rcpuser and rpcpassword hard to guess, you won't need to remember/use them for anything else, so feel free to smash the keyboard

**5.** Open wallet. Resync the whole wallet, from the menu "Tools" > "Wallet Repair" > "Rebuild Index"

**6.** Make sure the wallet is running and completely synced before continuing

## How to

To make it point to your primestone.conf, you have three options:

**A)** Create a file **sentinel.conf** in the same folder as the EXE with the following content:
primestone_conf=C:\path\to\primestone.conf

Start sentinel-win64.exe

**B)** From a console, execute the EXE by passing arguments 
sentinel-win64.exe --config=C:\path\to\primestone.conf

**C)** By creating a shortcut

1) Right click the sentinel-win64.exe, "Create Shortcut". 
2) Right click the shortcut, Properties
3) Edit Target and, at the end, add a SPACE and then "--config=C:\path\to\primestone.conf" INCLUDING the quotes "

Double click the shortcut to start sentinel.

## When everything fails
If you have followed all the steps and still get WATCHDOG_EXPIRED when issuing "masternode status":

**1.** Close the wallet

**2.** Delete all files inside "primestoneconf" except for "wallet.dat" and "primestone.conf".
**Please make sure you don't delete wallet.dat! Backup it, for real, that's your coins!**

**3.** Restart wallet, open sentinel-win64.exe, and let it sync!

### Feedback
If it doesn't work, create an *Issue* with detailed explanations


## Usage

Pick the appropiate file from [https://github.com/PrimeStonecoin/Sentinel/releases](Releases)

Open file `sentinel.conf` and change `primestone_conf` to point to your primestone configuration file

Run `sentinel.exe` and keep it open, that's all.

You might pass arguments to `sentinel.exe`, for example `sentinel.exe --config="C:\path\to\primestone.conf"`


# Building

Install pyinstaller `pip install pyinstaller`

Generate output EXE/ELF: `pyinstaller --onefile --paths=lib/ main.py`
