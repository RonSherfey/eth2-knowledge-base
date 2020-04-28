# Run with macOS using prysm.sh

####  [Official **PrysmaticLabs Docs**](https://docs.prylabs.network/docs/getting-started/)\*\*\*\*

#### Step 0.

**Homebrew installation**

Check if **Homebrew** is installed through the terminal.   
This can be done by pressing `CMD+Space` and searching for **Terminal**.

Run `brew help`.   
If the output is `command not found`, **Homebrew** needs to be installed, and if it matches the picture below **skip to Step 1.**  
  
In order to **install Homebrew** use the following code:  
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

![](../.gitbook/assets/image%20%2811%29.png)

**Step 1.**

**Install GPG**  
`brew install gnupg`

**Create the prysm directory:**  
`mkdir prysm`

**Enter the prysm directory:**  
`cd prysm`

**Get the prysm.sh script and make it executable:**  
`curl https://raw.githubusercontent.com/prysmaticlabs/prysm/master/prysm.sh --output prysm.sh && chmod +x prysm.sh`

**Step 2.**

**Start the beaconnode**  
`./prysm.sh beacon-chain`

**Wait** for the beaconnode to be in sync with the blockchain.   
This may take a few hours and you will see the following message:

`INFO initial-sync: Synced up to slot XXXXX`

**Step 3.**

**Create ETH2 Keys**  
`./prysm.sh accounts create--keystore-path=$HOME/eth2validator --password=yourPassword` 

![](../.gitbook/assets/image%20%283%29.png)

{% hint style="info" %}
The created Keys are now located in **$HOME/eth2validator** and can be accessed through the finder.
{% endhint %}

**Copy the Raw Transaction Data** and go to the [participation page](https://prylabs.net/participate).  
Some of the instructions on the participation page will be ignored because they are not required anymore. 

Follow the steps below to get Goerli ETH and to deposit them ****to activate your validator. If you cannot get any Goerli ETH through the participation page, join the [Prysm Discord](https://discord.gg/wJW7Rjk) channel.

![](../.gitbook/assets/image%20%2816%29.png)

**Step 4.**

**Start the validator**

`./prysm.sh beacon-chain --datadir=$HOME/prysm`

{% hint style="info" %}
The blockchain data is stored in the **$HOME/prysm** directory
{% endhint %}

**Step 5.**

Track your validator performance on [beaconcha.in](https://beaconcha.in/dashboard?validators=) with your public key \(orange\).   
Once the blockchain recognizes the deposit, the [beaoncha.in](https://beaconcha.in/) explorer will allow you to track the validator more accurately.

Wait for the inclusionSlot \(red\) to be reached. Once the blockchain has processed this slot, you will be staking! The Slot number can be tracked [here](https://beaconcha.in/blocks).

![](../.gitbook/assets/image%20%2819%29.png)

**Running multiple validators** 

Repeat **Step 4.** and **create more keys** into the same directory.   
**Use the same password for all keys.**

Copy the **Raw Transaction Data** for each validator, re-do the process on the [participation page](https://prylabs.net/participate) and deposit for each of them.

Once the system has received all deposits, you can just start a single validator window, and it will use **all** of the created keys \(=multiple validators\).
