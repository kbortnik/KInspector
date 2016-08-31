## Consistency issues

### Database consistency check

| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |

Runs DBCC CHECKDB on current database which checks all consistency issues (https://msdn.microsoft.com/en-us/library/ms176064.aspx).

### Documents consistency issues
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks that CMS_Tree and CMS_Document tables are without any consistency issues.

## Content

### Attachments by size
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays report of all attachments ordered by their size.  Storing files in a content tree can negatively affect website performance. If you're not using workflow or multilingual content features to manipulate those attachments, you can move them to the media library.  For more information, see the documentation: https://docs.kentico.com/display/K82/Defining+website+data+structure#Definingwebsitedatastructure-Storingdataefficiently

### Duplicate Page Aliases
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks that the CMS_DocumentAlias table does not contain any duplicates.


### Number of children of TreeNode
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays TreeNodes having more than 1000 children.  Our best practice is to store under each TreeNode maximum of 1000 children, otherwise it can negatively affect the performance.

### Page type is assigned to a site
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays page types used by a certain site without being assigned to this site.  If the page type is not assigned to the site and is used by this site, you will encounter problems while using import/export feature.

### Performance demanding web parts in transformations
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays transformations containing any of the following web parts: - CMSRepeater - CMSBreadCrumbs - CMSListMenu - CMSDataList  Having those web parts in a transformation can cause a significant performance hit as they load all the data from the database every time the transformation item is processed.  (e.g.: If you have 50 items processed in a transformation, you will end up with 50 database calls instead of 1)  You should use hierarchical transformation instead (see https://docs.kentico.com/display/K82/Using+hierarchical+transformations).

### Robots.txt
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks that the robots.txt file is present. See http://www.robotstxt.org/robotstxt.html for more details


## Event log
### Application restarts
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays information about application restarts.  Frequent restarts could signify some troubles.

### Event log errors
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays all errors from the event log.  In the ideal world, there should be no errors. If there are any, find a root cause and fix it to avoid this error happen again. Sometimes it's not possible to avoid all the errors, but that should be an exception.

### Event Log size
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Kentico recommends that the event log size is set around 5000-10,000 entries.  https://devnet.kentico.com/articles/maintenance-in-kentico

### Not found errors (404)
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays all the 404 errors from the event log.  If there are any 404 errors, there is a broken link somewhere on your website. Check the referrer URL and fix all the broken links.  You should avoid broken links on your website as it hurts SEO and generates unnecessary traffic.  For the complete website analysis, you can use an external tool like www.deadlinkchecker.com.


## Online marketing
### Contact groups with manual macro
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |     |  Y  |  Y  |  Y  |
Contact groups that have macro condition set via plain macro are always just slower and should be rewritten into MacroRuleDesigner, so that they can be translated into SQL queries to decrease recalculation time. For more, see https://docs.kentico.com/display/K82/Improving+custom+macro+performance+in+scoring+and+contact+groups  NOTE: This applies only on Kentico 8.1 and above, where the improvements were introduced.

### Inactive contact deletion settings
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks whether there is Online marketing module enabled and if so, checks the old contacts deletion settings. These are important to keep OM database smaller.

### Newsletters not using email queue (chance of losing emails)
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |     |  Y  |  Y  |  Y  |
Displays the newsletters (email campaigns) that are not using email queue.  If newsletter is not sent via email queue, emails are generated into memory queue, which could be lost on server restart. Default app pool recycle is every 29 hours. If you're sending a lot of emails, the probability is rather high.

### Size of the online marketing tables
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |     |  Y  |  Y  |  Y  |
Checks whether Online marketing tables aren't too big.  Checks the following:      * OM_Activity > 10 000 000,     * OM_Contact > 1 000 000,     * OM_ContactGroup > 50,     * OM_Rule > 50


## Performance
### Maximum 100 files per folder in Azure Blob storage
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Web sites utilizing Azure Blob storage should limit media library folder size to maximum 100 items per folder to achieve good performance.


## Security
### Flood Protection
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
This module checks to see if Flood Protection is enabled on the site. This module also checks to make sure Flood Protection is enabled for the Chat module in V8 and later. https://docs.kentico.com/display/K9/Flood+protection

### Password policy settings
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
It is critical that passwords are stored securely in the database, the module checks that the default and recommended SHA2 option is configured. https://docs.kentico.com/display/K9/Password+encryption+in+database This module also checks that there is a password policy enforced to ensure users use a password that meets a minimum set of requirements. https://docs.kentico.com/display/K9/Password+strength+policy+and+its+enforcement

### Security settings
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Some security settings need to be verified. If REST is enabled, verify all REST settings as there are known security flaws.

### Security web.config settings
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks security settings in web.config.

### SSL used for Administrative Interface
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks if pages of the administration interface are automatically redirected to https.

### Transformation analyzer
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Analyzes possible XSS vulnerabilities in transformations.

### Users with empty passwords
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Selects all users with empty passwords

### Users with plaintext passwords
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays a list of all users with passwords that are stored in plain text.  Passwords stored in plain text greatly increase the risk to users in the event that unauthorized users gain access your database and increase the risk that your site may be accessed through a brute force attack. By ensuring that all stored password are salted and hashed, you can significantly mitigate the damage done in the event of a database breach, and decrease the risk of unauthorized access to sensitive parts of your site.  For more information, see the documentation: https://docs.kentico.com/display/K82/Password+encryption+in+database

### Vulnerability analyzer
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Prints files which were added by the customer and their vulnerabilities.

### WebPart analyzer
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Analyzes possible vulnerabilities in web parts.


## Setup
### Add license key for 'localhost' domain NOTE: Edit the 'LicenseSetupModule.sql' first.
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Adds license key for 'localhost' domain, removes existing 'localhost' license key (if any).

### Assign all sites domain alias 'localhost'
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Assigns domain alias 'localhost' to all sites (deletes existing 'localhost' domain aliases).

### Disable enabled SMTP servers
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Disables SMTP servers defined either in the Settings or SMTP servers application.                  The servers are disabled by setting their server address to invalid value, so that servers disabled by the audit can be identified.

### Disable enabled Staging servers
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Disables Staging servers defined in the Staging application.  The servers are disabled by appending their URL with '.disabled', so that servers disabled by the audit can be identified. Setting the Enabled state of all servers to false would result in UI not being accessible (which might not be desired).

### Disable enabled Web farm servers
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Disables Web farm servers defined in the Web farm application.  The servers are disabled by setting their Enabled state to disabled and their display name is appended with '.disabled', so that servers disabled by the audit can be identified.

### Stop all sites
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Stops all running sites by setting their Status to 'STOPPED'. The IsOffline is left intact.


## Social marketing
### Expired tokens
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Checks that there are no expired tokens.


## (Uncategorised)
### Cache items
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Shows cache items and their size.

### CMSFile usage check (takes a while)
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |     |
Checks whethere there are unnecessary CMSFiles in the content tree

### Detailed analysis of all rendered pages (takes a while)
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |     |
Checks response time, response status, HTML size, ViewState size, number of links, favicons and Apple touch icons on the page.   Needs to have preset Url in the setup screen.  The favicon is checked as follows: The markup is analyzed for presence of <link> element specifying either 'icon' or 'shortcut icon' in its rel attribute. If multiple elements specifying favicon are found, all their hrefs are checked. When no explicit favicon is provided, the 'favicon.ico' in domain root is checked.  The Apple touch icons are checked as follows: The markup is analyzed for presence of <link> elements specifying either 'apple-touch-icon' or 'apple-touch-icon-precomposed' in their rel attribute. If multiple elements specifying touch icons are found, all their hrefs are checked. When no explicit touch icon is provided, no implicit icon is assumed, since there are many icon names to be tried (depending on device resolution, precomposed/standard icon version). For details on how the devices try to retrieve the implicit touch icon see https://mathiasbynens.be/notes/touch-icons#no-html  It is a good practice to provide explicit touch icons in the markup since only some browsers in some versions try to load implicit icons and the implicit paths differ in preferred resolution (the fallback with no version in its name is supported though). Note: Although it may seem that touch icon is for Apple devices only, this is not true. Android, BlackBerry and some other devices support it as well.

### Important scheduled tasks
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Selects important scheduled tasks

### Important settings
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Selects important settings from the database

### Kentico instance information
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |
Shows various information about the Kentico instance.

### Number of document aliases
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Returns number of aliases per node + total count of aliases and documents for direct comparison.  Having too many aliases per node may suggest problem with wrong API usage, decreased performance and SEO problems.   Huge amount of aliases also decrease site's performance. Only necessary aliases should be kept, the rest should be deleted.

### Old Web Farm Tasks
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |     |
As of Kentico 9 Web Farm health is monitored and managed, one of these features is that tasks are not generated after 24 hours.  Tasks that are older than 24 hours in age on Kentico 8.x and earlier versions indicate that there is a problem with the web farm health.  https://docs.kentico.com/display/K9/Troubleshooting+web+farms

### Page type fields data type mismatch
| Supported versions | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
You may face this error when exporting/importing a site or when working with web parts / widgets that list more than one-page type.  This error is caused by at least two different page types (for example A and B) having a field named in the same way (for example FieldName) but in each page type the field data is stored as a different data type (for example for A, it is 'Text' and for B it is 'GUID'). The best practice, in this case, is to use the page type code name as the Field name prefix. For example: CustomPageTypeA_FieldName  For more information, see https://devnet.kentico.com/articles/conversion-failed-when-converting-from-a-character-string-to-uniqueidentifier

### Screenshotter
| Supported versions | 5.5 | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|                    |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
It takes a screenshot of all published pages on the website.
 - All screenshots are saved into your desktop folder
 - You can see actual progress in a console window
 - For larger websites, it can take some time to take all the screenshots
 - Currently, it works only with the Firefox browser installed

NOTE: Current implementation will only take screenshots of the site you've entered in the first step (target instance setup). For pages that are not assigned to the that site it'll return 404s. You may ignore those.

### Site map
| Supported versions | 5.5 | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |     |  Y  |  Y  |  Y  |     |
Site map of the whole content tree

### Site templates
| Supported versions | 5.5 | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Analyzes all templates used on sites.

### Top 25 tables by size
| Supported versions | 5.5 | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays top 25 biggest tables from the database.

### Unspecified 'columns' setting in web parts
| Supported versions | 5.5 | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |  Y  |  Y  |  Y  |  Y  |  Y  |  Y  |
Displays list of web parts where 'columns' property is not specified.  Web parts without specified 'columns' property must load all field from the database.  By specifying this property, you can significantly lower the data transmission from database to the server and improve the load times.  For more information, see documentation: https://docs.kentico.com/display/K82/Loading+data+efficiently

### Workflow consistency
| Supported versions | 5.5 | 6.0 | 7.0 | 8.0 | 8.1 | 8.2 | 9.0 |
| ------------------ |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|                    |     |     |  Y  |  Y  |  Y  |  Y  |  Y  |
Checks if there are any inconsistencies between published data and data in CMS_Version history. Checks only custom fields stored in coupled table (excludes Document/Node properties)  Inconsistency can occur when a PUBLISHED document under WORKFLOW is updated in the API (when not creating/managing versions manually)  Implication of such inconsistency is that when you look at a document in Content tree, you see that it is published, but Live site shows different values. Solution is to re-save and re-publish the document 
