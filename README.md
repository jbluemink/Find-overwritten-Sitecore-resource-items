# Find-overwritten-Sitecore-resource-items
a Sitecore PowerShell Report for Sitecore IAR items, Items as Resources.

# For Sitecore 10.2, Sitecore 10.3+ and XM Cloud

IAR Sitecore items can be overwritten by a sql database item, With the Sitecore PowerShell report you can easy find the item and delete/restore the item as resource.

See blog [Items as resources by Sitecore part 2: reports](https://uxbee.nl/actueel/items-as-resources-by-sitecore-part-2)


## Download and Install the tool, Powershell Report
copy (items.master.iaroverwrittenreport.dat)  to \sitecore modules\items\master of your Sitecore CM instance.

## Install Sitecore Command Line Interface
See: [Install Sitecore Command Line Interface](https://doc.sitecore.com/xp/en/developers/103/developer-tools/install-sitecore-command-line-interface.html)

#cd {project folder}\
cd C:\projects\Find-overwritten-Sitecore-resource-items

dotnet new tool-manifest
dotnet nuget add source -n Sitecore https://sitecore.myget.org/F/sc-packages/api/v3/index.json \
#use the version you need or don't provide a version for the latest, note the 4.1.0 is old\
dotnet tool install Sitecore.CLI --version 4.1.0

#dotnet sitecore init

dotnet sitecore login --authority https://id.{host}.local --cm https://cm.{host}.local --allow-write true

#push item to Sitecore\
dotnet sitecore ser push

#pull sitecore item to files\
dotnet sitecore ser pull


## Genarate iar .dat file
dotnet sitecore itemres create -o iaroverwrittenreport


