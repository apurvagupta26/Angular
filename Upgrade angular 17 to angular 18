1. Ensure you are using a supported version of Node.js before upgrading your application. Angular v18 supports Node.js versions: v18.19.0 and newer.
2. Navigate to your application’s project directory and execute `ng update @angular/core@18 @angular/cli@18 — force` to update to Angular v18.
3. Next, update Angular Material by running `ng update @angular/material@18`.
4. follow the instructions in the Angular Update Guide to complete the update process
5. Handle Third-Party Dependencies:
 1.Third-party dependencies might need updates to be compatible with Angular 18. Check for any outdated packages:
   Run the following command to see outdated packages:
   npm outdated
   Update the outdated packages:
   npm update
   Some packages might require manual intervention if they have major updates or breaking changes. Check the documentation for each package for specific update instructions.
6. Update TypeScript Version
Angular 18 may require a specific TypeScript version. Ensure you have the correct TypeScript version installed:
Check the Angular documentation for the required TypeScript version.
Update TypeScript to the required version:
npm install typescript@<required_version>
Replace <required_version> with the version specified in the Angular documentation.
Once completed, your application will be upgraded.

Common Errors:
1. Error: ‘Hue “500” does not exist in palette. Available hues are: 0, 10, 20, 25, 30, 35, 40, 50, 60, 70, 80, 90, 95, 98, 99, 100, secondary, neutral, neutral-variant, error’
   Resolution:
    please update the following: 
    mat.define-palette to mat.m2-define-palette
    mat.define-typography-config to mat.m2-define-typography-config
    mat.define-light-theme to mat.m2-define-light-theme
    mat.define-dark-theme to mat.m2-define-dark-theme
    mat.red-palette to mat.$m2-red-palette
2. The Angular Compiler requires TypeScript >=5.4.0 and <5.5.2 but 5.5.2 was found instead
   Resolution: 
    npm install typescript@">=3.4.0 and <3.5.0" --save-dev
