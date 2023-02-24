<p align="center">
<img src="https://i.imgur.com/0NJwExP.png" alt="Azure Network Watcher Topology"/>
</p>

<h1>How to Setup VMs and a Virtual Network in Azure</h1>
This tutorial is desined to teach beginners how to create VMs and setup a Vnet in Azure, and then observe the etwork topology with Network Watcher.<br />

<h2>Pre-requisites </h2>

- [Setup a Subscription and a Resource in Azure for Beginner Labs](https://github.com/jacksonmalms/setup-azure-sub-and-resource)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Compute/Networking)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Linux (ubuntu server 20.04)

<h2>High-Level Steps</h2>

- Step 1: Create a Resource Group
- Step 2: Create a Windows 10 VM (While creating the VM, use the same resource group, and allow it to create a new Vnet and subnet)
- Step 3: Create a Ubuntu Server VM (While creating the VM, select the previously created resource group and Vnet)
- Step 4: Observe Your Virtual Network within Network Watcher
- Step 5: Either clean up the resources by deleting them, or you can keep them to use in the my next tutorial/lab, the link to that will be at the end of this tutorial!


<h2>Full Visual Walkthrough</h2>

<p>
<img src="https://i.imgur.com/iEMJNac.png"/>
</p>
<p>
First, log in to your Azure portal https://portal.azure.com/ (Assuming you already have an account with a subscription, but if you don't have one yet check the pre-requisites)
</p>
<br />

<p>
<img src="https://i.imgur.com/U00aXOd.png"/>
</p>
<p>
Next, create a new resource group, I named mine "RG-LAB-02", select whatever region that is closest to you. You can find the Resource Groups page (or any page in Azure) by searching for it in the searchbar at the top. Click Review + create, and then hit create.
</p>
<br />

<p>
<img src="https://i.imgur.com/z9N5Lnd.png"/>
</p>
<p>
Now go to the Virtual Machines page and create a new VM. I named mine "VM1-WINDOWS10", and make sure your VM's region is set to the same as your Resource Group and at the very least that is in the same region as the next VM that we will create, double check this right before you create the VM. Select Windows 10 Pro as the image.
</p>
<br />

<p>
<img src="https://i.imgur.com/7aM2MkO.png"/>
</p>
<p>
Now select the size and specs of the VM, I suggest selecting one with over 2GB of RAM or else it will just be way too slow (I just selected 2 CPUs and 16GB RAM). Then set the username and password, I highly suggest taking note of these. After that hit the check box under Licensing, and then hit next until you get to the networking section.
</p>
<br />

<p>
<img src="https://i.imgur.com/0Ma9Zeg.png"/>
</p>
<p>
Let the VM create it's own new Vnet, leave the subnet and public IP default, then click review and create.
</p>
<br />

<p>
<img src="https://i.imgur.com/7qRVqk8.png"/>
</p>
<p>
After the Windows VM deployment is complete, go back to the Virtual Machine page and start creating a new VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/zGyrGwn.png"/>
</p>
<p>
Set the resource group to the same one as the Windows VM, then name the VM, I named mine "VM2-UBUNTU". Make sure the region is set to the same as the last VM, select Ubuntu Server 20.04 LTS as your image, and use the x64 architecture.
</p>
<br />

<p>
<img src="https://i.imgur.com/KYFsdFn.png"/>
</p>
<p>
Now set the size of the VM, just use the same size as the previous one. Set the Authentication type to Password, then set the username and password of the VM.
Once you've done that, hit next until you get to the networking section.
</p>
<br />

<p>
<img src="https://i.imgur.com/P3rdouQ.png"/>
</p>
<p>
Select the Vnet as the same one as the Windows VM, mine is "VM1-WINDOWS10-vnet". Leave everything else default, just make sure everything looks like the screenshot above. Then hit review and create.
</p>
<br />

<p>
<img src="https://i.imgur.com/cfTtFxY.png"/>
</p>
<p>
Now we will try to view the network topology, to do this go to the Network Watcher page.
</p>
<br />

<p>
<img src="https://i.imgur.com/2H1mHwK.png"/>
</p>
<p>
Click on "Topology".
</p>
<br />

<p>
<img src="https://i.imgur.com/w1osZHS.png"/>
</p>
<p>
Select the resource group and Vnet that correspond to the ones we just created, and now we can see a visual representation of the network we just made!
Now we are finished, but if you you are unable to see the the topology and get a red text box instead, please proceed to the next step.
</p>
<br />

<p>
<img src="https://i.imgur.com/aicFPBL.png"/>
</p>
<p>
Go to the resource groups page and click on the "NetworkWatcherRG" resource group, and then click on the resource "NetworkWatcher_xyz".
</p>
<br />

<p>
<img src="https://i.imgur.com/vi5PTwv.png"/>
</p>
<p>
Hit the "move" button next to resource group.
</p>
<br />

<p>
<img src="https://i.imgur.com/xLnxt4L.png"/>
</p>
<p>
Select the resource group that the VMs are in, mine is "RG-LAB-02". Then hit next, it will then check to see if the resources are movable (it will be), and then wait a few minutes as it will take a while. Then get to the review section and apply the move. Again, this will take a few minutes.

After that go back to the Network Watcher page and go to the Topology section and it should now show up!

Congratulations, you made it to the end of this lab! Now you can either delete the resource groups to clean up, or keep the resources to proceed to the next lab/tutorial where we observe network traffic between the two VMs using wireshark.
- [Next Lab](https://github.com/jacksonmalms/azure-network-protocols)
</p>
<br />

<p>
<img src="https://i.imgur.com/ZttsXKR.png"/>
</p>
<p>
To delete the resource group, just go back to the resource groups page, click on the resource group, click delete resource group, and type/copy paste the resource group's name to confirm, and then click delete.
