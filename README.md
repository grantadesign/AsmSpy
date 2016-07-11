AsmSpy
------

A simple command line tool to view assembly references.

## Install 

Install [from Chocolatey package](https://chocolatey.org/packages/asmspy):

    C:\> choco install asmspy

Download [AsmSpy as a .zip here](http://static.mikehadlow.com/AsmSpy.zip). The .zip file contains AsmSpy.exe.

## How it works

Simply run AsmSpy giving it a path to your bin directory (the folder where your project's assemblies live).

    AsmSpy D:\Source\sutekishop\Suteki.Shop\Suteki.Shop\bin

It will output a list of all conflicting assembly references. That is where different assemblies in your bin folder reference different versions of the same assembly.

### Switches:
| Switch | Description |
| --- | --- |
| all | list all assemblies and references.<br> Supported formats:  /a, all, /all |
| nonsystem | list system assemblies. <br> Supported formats:  /n, nonsystem, /nonsystem |

### Examples
To see a list of all assemblies and all references, just add the 'all' flag:

    AsmSpy D:\Source\sutekishop\Suteki.Shop\Suteki.Shop\bin all
    
To ignore system assemblies, add the 'nonsystem' flag.

The output looks something like this:


	Reference: System.Runtime.Serialization
		3.0.0.0 by Microsoft.ServiceModel.Samples.XmlRpc
		3.0.0.0 by Microsoft.Web.Mvc
		4.0.0.0 by Suteki.Shop
	Reference: System.Web.Mvc
		2.0.0.0 by Microsoft.Web.Mvc
		3.0.0.0 by MvcContrib
		3.0.0.0 by MvcContrib.FluentHtml
		3.0.0.0 by Suteki.Common
		2.0.0.0 by Suteki.Common
		3.0.0.0 by Suteki.Shop
		2.0.0.0 by Suteki.Shop
	Reference: System.ServiceModel.Web
		3.5.0.0 by Microsoft.Web.Mvc
	Reference: System.Web.Abstractions
		3.5.0.0 by Microsoft.Web.Mvc


You can see that System.Web.Mvc is referenced by 7 assemblies in my bin folder. Some reference 
version 2.0.0.0 and some version 3.0.0.0. I can now resolve any conflicts.

