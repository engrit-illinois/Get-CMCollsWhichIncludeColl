# Get-CMCollsWhichIncludeColl.psm1

This is a module that takes a target collection name and returns all collections which include the target collection.  
Including the `-GetDeployments` parameter will also retrieve all deployments to the returned collections.  
Note: this will take ~3+ minutes to complete in our environment.  

This is useful because the GUI admin console does not provide a native way to see this data.  

### Example usage

1. Download `Get-CMCollsWhichIncludeColl.psm1` to `$HOME\Documents\WindowsPowerShell\Modules\Get-CMCollsWhichIncludeColl\Get-CMCollsWhichIncludeColl.psm1`.
2. Run it. It's recommended to save the results to a variable.
  - e.g. `$collections = Get-CMCollsWhichIncludeColl "UIUC-ENGR-IS EWS" -GetDeployments`
3. Access returned data.
  - e.g. Get names of returned collections: `$collections.Name | Sort`
  - e.g. Get names of applications deployed to returned collections: `$collections._Deployments.ApplicationName | Sort`

### Parameters

#### -Loud
Optional switch.  
If specified, logs progress to the console.  
If omitted, module is silent.  

#### -GetDeployments
Optional switch.  
If specified, additionally retrieves deployments to returned collections.  

#### -SiteCode
Optional string. Recommend leaving default.  
The site code of the MECM site to query.  
Default is `MP0`.  

#### -Provider
Optional string. Recommend leaving default.  
The SMS provider machine name.  
Default is `sccmcas.ad.uillinois.edu`.  

#### -CMPSModulePath
Optional string. Recommend leaving default.  
The path to the ConfigurationManager Powershell module installed on the local machine (as part of the admin console).  
Default is `$($ENV:SMS_ADMIN_UI_PATH)\..\ConfigurationManager.psd1`.  

# Notes
- Feature suggestion for this: https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15827071-collection-deployment
- By mseng3. See my other projects here: https://github.com/mmseng/code-compendium.
