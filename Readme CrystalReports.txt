							README
						        ======	

					CrystalReports(TM) V.13.0.0.16 Integration
                                        -------------------------------------------

Contents
--------

1.About
2.Requirements
3.Software/Plugin Downloads
4.Installation
5.Recommended Modules
5.Configuration
6.Troubleshooting
7.FAQ

ABOUT
=====
=>SAP Crystal Reports, developer version for Microsoft Visual Studio

SAP Crystal Reports2013(Crystal Reports) is designed to work with your database to help you analyze
and interpret important information. Crystal Reports makes it easy to create simple reports, and, it also
has the comprehensive tools you need to produce complex or specialized reports.

REQUIREMENTS
============
1.Operating Systems
-------------------   
	Windows 7,8,8.1,10

2.H/W Req:
----------
	i)Design Time(Design Time refers to the Crystal Reports integration with Microsoft Visual Studio IDE)
		=>1.6Ghz or faster processor,
		=>1 GB (32 Bit) or 2 GB (64 Bit) RAM ,
		=>650MB (32-bit) or 1.1GB (64-bit) available hard drive space

	ii)Runtime(refers to the runtime components that can be deployed to client environments.)
		=>Intel Pentium III or faster processor,
		=>512 MB RAM,
		=>300MB (32-bit) or 325MB (64-bit) available hard drive space

3.Supported VisualStudio Versions
---------------------------------
	Vs2012,Vs2013,Vs2015

4.Supported Application Servers
-------------------------------
	IIS 7.5 on Windows 7,
	IIS 7.5 on Windows Server 2008 R2,
	IIS 8 on Windows 8,
	IIS 8 on Windows Server 2012,
	IIS 8.5 on Windows 8.1,
	IIS 8.5 on Windows Server 2012 R2,
	IIS 10 on Windows 10,
	IIS Express.

5.Supported Browsers
--------------------
	Internet Explorer 8,9,10,11
	FireFox,
	GoogleChrome,
	MsEdge,
	Safari.


SOFTWARE/PLUGIN DOWNLOADS
=========================

1.Open this link - http://scn.sap.com/docs/DOC-7824
2.Select SupportPack for 16 and Download the "Install Executable" File


INSTALLATION
============

*Install as you would normally install the exe software.

Note
====
InstallExecutable(.exe) file installs the desgin time and runtime software as well.(Make sure you install both)


RECOMMENDED MODULES
===================
	1.Admin
	2.Billing
	3.POS
	4.DC
	5.BackOffice


CONFIGURATION
=============

=>Crystal Report Viewer does not display reports if it is not configured properly
=>Crystal Report requires few configurations to be added into the web.config files.Some of them are inserted when you add a Crystal Report to the Project.
=>The following elements are unique to SAP Crystal Reports and may be added to your Web.Config file.

<configSections>
 <!--CrystalReportViewer-->
    <sectionGroup name="businessObjects">
      <sectionGroup name="crystalReports">
        <section name="rptBuildProvider" type="CrystalDecisions.Shared.RptBuildProviderHandler, CrystalDecisions.Shared, Version=13.0.2000.0, Culture=neutral, PublicKeyToken=692fbea5521e1304, Custom=null"/>
        <section name="crystalReportViewer" type="System.Configuration.NameValueSectionHandler"/>
      </sectionGroup>
    </sectionGroup>
 </configSections>

Setting up Viewers Virtual Directory
------------------------------------
=>Crystal Reports Require Viewers Virtual Directory is setup correctly on the development as well as production web servers.  
=>Crystal Reports relies on a virtual directory to access viewers to display the report. 
=>The virtual directory and its underlying file path are unique for each version of SAP Crystal Reports and 
  that way, succeeding versions of SAP Crystal Reports on the same machine work without conflict.

=>Add the following Sections in your web.config file

<!--#Setting CRV Path#-->
  <businessObjects>
    <crystalReports>
      <rptBuildProvider>
        <add embedRptInResource="true"/>
      </rptBuildProvider>
      <crystalReportViewer>
        <add key="ResourceUri" value="../crystalreportviewers13"/>  -->//Crystal Report Viewer Path
      </crystalReportViewer>
    </crystalReports>
  </businessObjects>

NOTE
====
i)Development Server Virtual Directory
------------------------------------
=>If you are using CRs in local machine set the virtual path to

/Windows/Microsoft.NET/Framework/v4.0.30319/ASP.NETClientFiles/crystalreportviewers13

ii)Production Virtual Directory (IIS)
-------------------------------------
=> if you are using CRs in WebServer set the virtual path to

/inetpub/wwwroot/aspnet_client/system_web/4_0_30319/crystalreportviewers13

or

/aspnet_client/system_web/4_0_30319/crystalreportviewers13
							


FAQs & TROUBLESHOOTING
======================

*If the Crystal Reports does not display, do the following
----------------------------------------------------------

1.Go to  C:\Program files (X86)  -> Sap Business Objects -> Crystal Reports for Net Framework 4.0 -> Common ->Crystal reports 2011 -> crystalreportviewers
2.Copy the entire crystalreportviewers folder.
3.Paste it into root of your module or application

==>These steps will ensure that reports are rendered correctly in your development or Production servers	

*Still unable to view reports ??
---------------------------------

Make sure CR.exe is installed correctly.
Make sure the user has sufficient previlege to access the crystalreportviewers13 folder.

*For More FAQs Visit
--------------------

http://scn.sap.com/community/crystal-reports-for-visual-studio


