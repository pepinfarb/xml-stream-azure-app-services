# xml-stream-azure-app-services
Precompiled NodeJS native module for use on Azure App Service

Azure App Services does not play well with all NodeJS native modules.
XML-STREAM is dependent upon NODE-EXPAT which will compile on an Azure virtual machine *with the right setup :)*
It will however not compile on an App Service.

To accomplish this we removed xml-stream from our package.json, and precompiled it with: npm install xml-stream --arch=ia32
The we simply zipped it and put it in a 'native_modules' directory. Then upon deployment our Kudu script first runs npm install so the package.json items are installed, then unzips the file into the 'node_modules/xml-stream' directory.

Works like a charm.




