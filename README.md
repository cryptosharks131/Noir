# NOIR
Shell script to install a [Noirnode](https://noirofficial.org/) on a Linux server running Ubuntu 16.04.  
This will require a VPS, I use [Vultr](https://www.vultr.com/?ref=7310394).  I recommend using a $5 server.
This script will install **Noir Core 2.1.0.8**.
***

## Installation:
Log into the server using ssh (Putty for windows or terminal for Mac users) and run the following commands:
```
wget -q https://raw.githubusercontent.com/cryptosharks131/Noir/master/noir_install.sh
bash noir_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows/Mac Wallet:
1. Open the Noir Core Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **25000** **NOIR** to **MN1**.
4. Wait for 15 confirmations before starting the node.
5. Go to **Help -> "Debug window - Console"**
6. Type the following command: **noirnode outputs**
7. Open noirnode.conf from the following folder %appdata%\noir (windows) or ~/Library/Application Support/ (hidden folder for Mac users)
8. Add the following entry:
```
Alias Address Genkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:6214**
* Genkey: **Noirnode GenKey**
* TxHash: **First value from Step 6** 
* Output index:  **Second value from Step 6** It can be **0** or **1**
9. Click OK and exit the Wallet.
10. Open Noir Core Wallet, go to **Noirnode Tab**.
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again.
10. Click **Start All** or **Start Alias**
11. If you are not able to see your **Noirnode**, try to close and open your desktop wallet.
***

## Usage:
```
noir-cli getinfo
noir-cli noirnode status
noir-cli noirsync status
```
Also, if you want to check/start/stop **NOIR** , run one of the following commands as **root**:
```
systemctl status Noir #To check the service is running.
systemctl start Noir #To start Noir service.
systemctl stop Noir #To stop Noir service.
systemctl is-enabled Noir #To check whetether Noir service is enabled on boot or not.
```
***

## Updating Noir
The first line (rm noir_update.sh) is not required the very first time you update the node and will return an error if you run it.  This is fine, continue with the update script.
```
rm noir_update.sh*
wget -q https://raw.githubusercontent.com/cryptosharks131/Noir/master/noir_update.sh
bash noir_update.sh
```
***

## Donations:  
**BTC**: 1FJvtLBszQgY2eKBawov48RwSYy2yqEvn1  
**ETH**: 0x39acE9917e25E2A04643d30319cF34449A72441B  
**LTC**: LR1Mmchr6Zz1vj51xecTiEdS1WHfJTVg5t
