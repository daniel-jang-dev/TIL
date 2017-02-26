###Updating Angular CLI
If you're using Angular CLI beta.28 or less, you need to uninstall angular-cli package. It should be done due to changing of package's name and scope from angular-cli to @angular/cli:

    npm uninstall -g angular-cli
    npm uninstall --save-dev angular-cli
To update Angular CLI to a new version, you must update both the global package and your project's local package.

Global package:

    npm uninstall -g @angular/cli
    npm cache clean
    npm install -g @angular/cli@latest

Local project package:

    rm -rf node_modules dist (# use rmdir on Windows)
    npm install --save-dev @angular/cli@latest
    npm install
