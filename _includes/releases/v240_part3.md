### Passbolt API (All)
#### Added
- PASSBOLT-2972: As LU I should be able to delete multiple passwords in bulk
- PASSBOLT-2951: Merge the remember me on CE
- PASSBOLT-2329: As an administrator deleting a group which is sole owner of one or several passwords, I should be requested to select a new owner for these passwords
- PASSBOLT-2972: As LU I should be able to select multiple passwords with standard keyboard interactions (command and shift keys)

#### Improved
GITHUB#275: Adding SSL configuration environment variables for cake mysql driver
- PASSBOLT-2534: As LU I should not be able to copy to clipboard empty login/url
- PASSBOLT-2017: As LU when I save a password (create/edit) the dialog shouldn't persist until the request is processed by the API
- PASSBOLT-3073: As LU I should get a visual feedback directly after filtering the passwords or the users workspace
- PASSBOLT-3009 Add types to authentication tokens

#### Fixed
- PASSBOLT-2966: As LU I can't see passwords shared with me clicking on the "shared with me" shortcut filter
- GITHUB#246: Fix healthcheck tips relative to tmp folder
- PASSBOLT-3063: Fix appjs base url and subfolder
- PASSBOLT-3074: As a logged in user selecting a "remember me" duration the checkbox should be selected automatically
- PASSBOLT-2976: Fix API requests issues when the user is going to another workspace
- PASSBOLT-3082: ezyang/htmlpurifier cache should be stored in the application cache directory
- PASSBOLT-2982: Fix session expired check
- PASSBOLT-3086: As LU when I have 100+ passwords I cannot see the passwords after the 100th more than once

#### Passbolt CLI
- \#17 Display more meaningful error messages on configuration issues
- \#16 Fix user index when current user is an admin
- Update dependencies and improve Readme

