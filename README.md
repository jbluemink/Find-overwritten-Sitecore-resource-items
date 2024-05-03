# Find-overwritten-Sitecore-resource-items
- A Sitecore PowerShell Report for Sitecore IAR items, Items as Resources.
- Identify Which Items Are From Resource Files (IAR) and Database
- A Content Editor warning for IAR items and IAR overridden, overwritten items in Sitecore PowerShell
- A overwritten resource item compare in the Report
- A overwritten resource item restore/delete in the Report
- A package resource item in the Report
- A Items as Resources, IAR Gutter with compare / resource file lookup.

### Recent Updates:
- 30 Sep 2023 Add package option in report.
- 2 Jan 2024 Add support for core database and web for non XM Cloud
- 16 March 2024 support fot Azure webapps
- 30 March 2024 support for multiple file
- 1 April 2024 add itemdefinition to the compare

## PowerShell only
Certainly with Sitecore XM Cloud there is more resistance to extend the Sitecore CMS using c# code in a custom DLL. But with Sitecore PowerShell a lot can be done these tools are completely in Sitecore PowerShell and everything is in Sitecore items no files needed.

## For Sitecore 10.2, Sitecore 10.3+ and XM Cloud
IAR Sitecore items can be overwritten by a sql database item, With the Sitecore PowerShell report you can easy find the item and delete/restore the item as resource.

![Example](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/find-overwritten-sitecore-resource-items.png)

![compare-Example](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/iar-compare-report.png)
See blog 
- [Items as resources by Sitecore part 6: translation files and update item definitions](https://uxbee.nl/insights/items-as-resources-by-sitecore-part-6)
- [Create a Package Containing Overridden IAR Items](https://www.stockpick.nl/sitecore/create-a-package-containing-overridden-items/)
- [Items as resources by Sitecore part 5: gutter](https://uxbee.nl/insights/items-as-resources-by-sitecore-part-5)
- [Items as resources by Sitecore part 4: compare](https://uxbee.nl/insights/items-as-resources-by-sitecore-part-4)
- [Items as resources by sitecore part 3: restoring](https://uxbee.nl/insights/items-as-resources-by-sitecore-part-3)
- [Items as resources by Sitecore part 2: reports](https://uxbee.nl/insights/items-as-resources-by-sitecore-part-2)
Based on the first version of this tool. See [gist](https://gist.github.com/jbluemink/ac0851a20a3e94a25a6d998dcd25f466)

See the Compare in action
- [YouTube Tools for working with Sitecore Items as Resources - Compare Items](https://www.youtube.com/watch?v=8AHDOQr2zsA)

See the gutter in action
- [YouTube Sitecore Items as Resources - IAR gutter](https://youtu.be/yAUxVGcWlp0)

## IAR Content Editor Warning for Sitecore 10.3+ and XM Cloud.
See blog : [Item as resources PowerShell Content Editor Warning](https://www.stockpick.nl/sitecore/item-as-resources-powershell-warning/)

![Example](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/Overridden-item-as-resource-content-editor-warning.png)

## IAR Gutter for Sitecore 10.3+ and XM Cloud.
To enable, in Sitecore Shell, bottom left corner start button, click, PowerShell Toolbox, Rebuild script intergration points.
Enable IAR Gutter in Sitecore content editor, right mouse click in the left from the Tree, enable IAR Gutter

![IAR-Gutter](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/sitecore-iar-gutter-with-resource-file-lookup-compare.png)

# TODO
- Add file/item/fields viewer.

# Installing
3 options for installing this tool, choose the option you like 

## option 1) Download and Install the tool, Powershell Report
For just installing and use the tool the easy way is:
copy items.master.iaroverwrittenreport.dat  to \sitecore modules\items\master of your Sitecore CM instance.

## option 2) For using the Sitecore CLI and optional using Visual Studio to edit the module.json
### Install Sitecore Command Line Interface
See: [Install Sitecore Command Line Interface](https://doc.sitecore.com/xp/en/developers/103/developer-tools/install-sitecore-command-line-interface.html) \
Note: You must have .NET 6 installed on your workstation before installing the Sitecore CLI.

#cd {project folder}\
cd C:\projects\Find-overwritten-Sitecore-resource-items

dotnet new tool-manifest
dotnet nuget add source -n Sitecore https://nuget.sitecore.com/resources/v3/index.json \
dotnet tool install Sitecore.CLI --version 5.1.25

#dotnet sitecore init

dotnet sitecore login --authority https://id.{host}.local --cm https://cm.{host}.local --allow-write true

#push item to Sitecore\
dotnet sitecore ser push

#pull sitecore item to files\
dotnet sitecore ser pull


### Generate IAR .dat file
For developers if you made changes and want to update the .dat file
dotnet sitecore itemres create -o iaroverwrittenreport

## option 3) Install the package zip
first option too much hassle, hey this is even easier with an old fashioned sitecore zip package
Download Find-overwritten-Sitecore-resource-items-{DATE}.zip  and use the sitecore package installer.
In desktop, Development Tools, Installation Wizard

# Tips
When you get very quick a Message "The data for the dialog is not available. Either your server was restarted or the server cache was flushed. If this is a recurring problem, contact your system administrator."
one reason could be low on memory when running Docker default container size is max 1 GB memory. add mem_limit: 4GB in the docker-compose.override.yml for the CM container.
