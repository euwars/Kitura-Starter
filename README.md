![Kitura](https://raw.githubusercontent.com/IBM-Swift/Kitura/master/Documentation/KituraLogo.png)

[![Build Status - Master](https://travis-ci.org/IBM-Bluemix/Kitura-Starter.svg?branch=master)](https://travis-ci.org/IBM-Bluemix/Kitura-Starter)
[![Join the chat at https://gitter.im/IBM-Swift/Kitura](https://badges.gitter.im/IBM-Swift/Kitura.svg)](https://gitter.im/IBM-Swift/Kitura?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![macOS](https://img.shields.io/badge/os-Mac%20OS%20X-green.svg?style=flat)](http://www.apple.com/macos/)
[![Linux](https://img.shields.io/badge/os-linux-green.svg?style=flat)](http://releases.ubuntu.com/14.04/)
[![Apache 2](https://img.shields.io/badge/license-Apache2-blue.svg?style=flat)](https://www.apache.org/licenses/LICENSE-2.0)
[![Bluemix Deployments](https://deployment-tracker.mybluemix.net/stats/f3517b364e8ee44775acaf9cece55f6c/badge.svg)](https://deployment-tracker.mybluemix.net/)

**Bluemix starter application for Kitura web framework and HTTP server**

## What is Kitura?
[Kitura](https://github.com/IBM-Swift/Kitura) is a new, modular, package-based web framework written in the Swift language, that allows you to build web services with complex routes, easily.

## Kitura-Starter Overview
Kitura-Starter is a [Kitura](https://github.com/IBM-Swift/Kitura) based server application that you can use as a starting point to get your own Kitura application up and running on Bluemix. Also, if you'd like to run this app locally, you can do so on your [macOS](http://www.apple.com/osx/) or [Ubuntu 14.04](http://www.ubuntu.com/download) system.

## Application Requirements
To compile and run this starter application on your local system, you need to install the [Swift compiler](https://swift.org/download/) for your platform. This version of Kitura-Starter works with the Swift `3.1` release binaries. Compatibility with other Swift versions is not guaranteed.

For further details on executing Kitura-based applications locally, please see Kitura's instructions for installation on [macOS ](https://github.com/IBM-Swift/Kitura#installation-os-x) and on [Linux](https://github.com/IBM-Swift/Kitura#installation-linux-apt-based) since system level dependencies may be required before attempting to execute this starter app.

If you are interested in manually deploying the application to Bluemix, you'll need to install the Cloud Foundry [command line](https://docs.cloudfoundry.org/devguide/cf-cli/install-go-cli.html) on your system.  Once it is installed, you can use it to [authenticate and access](https://www.ng.bluemix.net/docs/starters/install_cli.html) your Bluemix organization(s) and spaces.  You can find further details on how to deploy this sample application to Bluemix in a subsequent section.

## Clone, build, and run locally
Once you have installed the Swift compiler and any system level dependencies required by the Kitura framework, you can proceed with the steps described in this section.

1) Clone this repo using `git clone https://github.com/IBM-Bluemix/Kitura-Starter.git`.

2) Go to the root folder of this repo on your system and issue the `swift build` command to compile the application:

```
$ swift build
Compile Swift Module 'Socket' (3 sources)
Compile Swift Module 'SwiftyJSON' (2 sources)
Compile Swift Module 'LoggerAPI' (1 sources)
Compile Swift Module 'KituraTemplateEngine' (1 sources)
Compile Swift Module 'HeliumLogger' (1 sources)
Compile Swift Module 'SSLService' (1 sources)
Compile Swift Module 'CloudFoundryEnv' (7 sources)
Compile CHTTPParser utils.c
Compile CHTTPParser http_parser.c
Linking CHTTPParser
Compile Swift Module 'KituraNet' (34 sources)
Compile Swift Module 'CloudFoundryDeploymentTracker' (1 sources)
Compile Swift Module 'Kitura' (41 sources)
Compile Swift Module 'Kitura_Starter' (2 sources)
Linking ./.build/debug/Kitura-Starter
```

Once the application is compiled, you can start the server (note that the executable file is located in the `.build/debug` directory: `./.build/debug/Kitura-Starter`):

```
$ ./.build/debug/Kitura-Starter
 INFO: Kitura_Starter main.swift line 29 - Server will be started on 'http://localhost:8080'.
 INFO: listen(on:) HTTPServer.swift line 73 - Listening on port 8080
```

Once the server starts, you should see the message _Listening on port 8080_ as shown above.

3) Open your browser at [http://localhost:8080](http://localhost:8080) to access the welcome page for the Kitura-Starter app. This page displays static HTML content served from the Kitura-based server application. You can explore the `public` folder in the repo to see the HTML file and related resources (e.g. images, CSS file)

4) To access a plain text greeting, point your browser to [http://localhost:8080/hello](http://localhost:8080/hello).

5) To perform a `POST` operation, use your preferred REST client (e.g. [Postman](https://www.getpostman.com/)) to send a string to [http://localhost:8080/hello](http://localhost:8080/hello). You should get a text response that includes the string you sent to the endpoint.

6) To receive a JSON payload, point your browser to [http://localhost:8080/json](http://localhost:8080/json).

## Pushing the application to Bluemix
### Using the Deploy to Bluemix button
Clicking on the button below deploys this starter application to Bluemix. The `manifest.yml` file [included in the repo] is parsed to obtain the name of the application and configuration details. For further details on the structure of the `manifest.yml` file, see the [Cloud Foundry documentation](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#minimal-manifest).

<!---
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy)
-->
[![Deploy to Bluemix](https://deployment-tracker.mybluemix.net/stats/f3517b364e8ee44775acaf9cece55f6c/button.svg)](https://bluemix.net/deploy?repository=https://github.com/IBM-Bluemix/Kitura-Starter.git)

Once deployment to Bluemix is completed, you can access the route assigned to your application using the web browser of your choice. You should then see the welcome page for the Kitura-Starter app! To access a plain text greeting, point your browser to `http://<application_route>/hello`. To perform a `POST` operation, use your preferred REST client (e.g. [Postman](https://www.getpostman.com/)) to send a string to `http://<application_route>/hello`. You should get a text response that includes the string you sent to the endpoint. Finally, to receive a JSON payload, point your browser to `http://<application_route>/json`.

Note that the [IBM Bluemix buildpack for Swift](https://github.com/IBM-Swift/swift-buildpack) is used for the deployment of this app to Bluemix. This IBM Bluemix buildpack for Swift is currently installed in the following Bluemix regions: US South, United Kingdom, and Sydney.

### Using the Cloud Foundry command line
You can also manually deploy the app to Bluemix. Though not as magical as using the Bluemix button above, manually deploying the app gives you some insights about what is happening behind the scenes. Remember that you'd need the Cloud Foundry [command line](https://www.ng.bluemix.net/docs/starters/install_cli.html) installed on your system to deploy the app to Bluemix.

Using the Cloud Foundry command line you can get a list of the buildpacks (along with their versions) that are installed on Bluemix. Note that you should be already logged on to Bluemix before you issue any of the following commands.

Executing the `cf buildpacks` above command should result in output similar to the following:

```
$ cf buildpacks
Getting buildpacks...

buildpack                              position   enabled   locked   filename
liberty-for-java                        1          true      false    buildpack_liberty-for-java_v3.8-20170308-1507.zip
sdk-for-nodejs                          2          true      false    buildpack_sdk-for-nodejs_v3.11-20170303-1144.zip
swift_buildpack                         3          true      false    buildpack_swift_v2.0.5-20170328-1639.zip
dotnet-core                             4          true      false    buildpack_dotnet-core_v1.0.10-20170124-1145.zip
java_buildpack                          5          true      false    java-buildpack-v3.13.zip
ruby_buildpack                          6          true      false    ruby_buildpack-cached-v1.6.34.zip
nodejs_buildpack                        7          true      false    nodejs_buildpack-cached-v1.5.29.zip
go_buildpack                            8          true      false    go_buildpack-cached-v1.7.18.zip
python_buildpack                        9          true      false    python_buildpack-cached-v1.5.15.zip
php_buildpack                           10         true      false    php_buildpack-cached-v4.3.27.zip
xpages_buildpack                        11         true      false    xpages_buildpack_v1.2.5-20170320-2106.zip
staticfile_buildpack                    15         true      false    staticfile_buildpack-cached-v1.3.17.zip
binary_buildpack                        16         true      false    binary_buildpack-cached-v1.0.9.zip
swift_v2_0_2-20161118-1326              21         true      false    buildpack_swift_v2.0.2-20161118-1326.zip
dotnet-core_v1_0_6-20161205-0912        22         true      false    buildpack_dotnet-core_v1.0.6-20161205-0912.zip
sdk-for-nodejs_v3_11-20170206-1113      23         true      false    buildpack_sdk-for-nodejs_v3.11-20170206-1113.zip
liberty-for-java_v3_7-20170118-2046     24         true      false    buildpack_liberty-for-java_v3.7-20170118-2046.zip
xpages_buildpack_v1_2_3-20170315-1027   25         true      false    xpages_buildpack_v1.2.3-20170315-1027.zip
dotnet_core_buildpack                   26         true      false    dotnet-core_buildpack-cached-v1.0.11.zip
swift_buildpack_v2_0_4-20170125-2344    27         true      false    buildpack_swift_v2.0.4-20170125-2344.zip
```

Looking at the output above, we can see that the IBM Bluemix buildpack for Swift is installed on Bluemix. This will allow a seamless deployment of the starter application to Bluemix.

After you have cloned this Git repo, go to its root folder on your system and issue the `cf push` command:

```
$ cf push
Using manifest file /Users/olivieri/git/Kitura-Starter/manifest.yml

Creating app Kitura-Starter in org roliv@us.ibm.com / space dev as roliv@us.ibm.com...
OK

Creating route kitura-starter-unsanctified-intervalometer.mybluemix.net...
OK

Binding kitura-starter-unsanctified-intervalometer.mybluemix.net to Kitura-Starter...
OK

Uploading Kitura-Starter...
Uploading app files from: /Users/olivieri/git/Kitura-Starter
Uploading 28K, 17 files
Done uploading               
OK

Starting app Kitura-Starter in org roliv@us.ibm.com / space dev as roliv@us.ibm.com...
Downloading swift_buildpack...
Downloaded swift_buildpack
Creating container
Downloading app package...
Downloaded app package (27.7K)
Staging...
-----> Buildpack version 2.0.5
-----> Default supported Swift version is 3.1
-----> Copying deb files to installation folder...
-----> No Aptfile found.
-----> Configure for apt-get installs...
-----> Writing profile script...
-----> Getting swift-3.1
       Cached swift-3.1
-----> Unpacking swift-3.1.tar.gz
-----> Getting clang-3.8.0
       Cached clang-3.8.0
-----> Unpacking clang-3.8.0.tar.xz
-----> .ssh directory and config file not found.
-----> Fetching Swift packages and parsing Package.swift files...
-----> Skipping cache restore (new swift signature)
       Fetching https://github.com/IBM-Swift/HeliumLogger.git
       Fetching https://github.com/IBM-Swift/Configuration.git
       Fetching https://github.com/IBM-Swift/CloudConfiguration.git
       Fetching https://github.com/IBM-Swift/BlueSocket.git
       Cloning https://github.com/IBM-Swift/Configuration.git
       Resolving https://github.com/IBM-Swift/Configuration.git at 0.2.4
       Cloning https://github.com/IBM-Swift/Kitura.git
       Resolving https://github.com/IBM-Swift/BlueSSLService.git at 0.12.30
       Resolving https://github.com/IBM-Swift/LoggerAPI.git at 1.6.0
       Fetching https://github.com/IBM-Bluemix/cf-deployment-tracker-client-swift.git
       Fetching https://github.com/IBM-Swift/CCurl.git
       Fetching https://github.com/IBM-Swift/Kitura-TemplateEngine.git
       Cloning https://github.com/IBM-Swift/CEpoll.git
       Resolving https://github.com/IBM-Swift/CEpoll.git at 0.1.0
       Resolving https://github.com/IBM-Swift/HeliumLogger.git at 1.6.1
       Cloning https://github.com/IBM-Swift/Kitura-net.git
       Cloning https://github.com/IBM-Bluemix/cf-deployment-tracker-client-swift.git
       Resolving https://github.com/IBM-Swift/BlueSocket.git at 0.12.41
       Fetching https://github.com/IBM-Swift/Kitura.git
       Fetching https://github.com/IBM-Swift/CEpoll.git
       Fetching https://github.com/IBM-Swift/Kitura-net.git
       Fetching https://github.com/IBM-Swift/BlueSSLService.git
       Fetching https://github.com/IBM-Swift/Swift-cfenv.git
       Fetching https://github.com/IBM-Swift/OpenSSL.git
       Fetching https://github.com/IBM-Swift/LoggerAPI.git
       Fetching https://github.com/IBM-Swift/SwiftyJSON.git
       Cloning https://github.com/IBM-Swift/Swift-cfenv.git
       Resolving https://github.com/IBM-Swift/Swift-cfenv.git at 4.0.0
       Cloning https://github.com/IBM-Swift/CCurl.git
       Resolving https://github.com/IBM-Swift/CCurl.git at 0.2.3
       Resolving https://github.com/IBM-Swift/Kitura.git at 1.6.3
       Cloning https://github.com/IBM-Swift/OpenSSL.git
       Resolving https://github.com/IBM-Swift/OpenSSL.git at 0.3.1
       Cloning https://github.com/IBM-Swift/HeliumLogger.git
       Cloning https://github.com/IBM-Swift/BlueSSLService.git
       Resolving https://github.com/IBM-Swift/Kitura-net.git at 1.6.2
       Resolving https://github.com/IBM-Bluemix/cf-deployment-tracker-client-swift.git at 3.0.0
       Cloning https://github.com/IBM-Swift/CloudConfiguration.git
       Resolving https://github.com/IBM-Swift/CloudConfiguration.git at 2.0.0
       Cloning https://github.com/IBM-Swift/BlueSocket.git
       Cloning https://github.com/IBM-Swift/SwiftyJSON.git
       Resolving https://github.com/IBM-Swift/SwiftyJSON.git at 15.0.6
       Cloning https://github.com/IBM-Swift/LoggerAPI.git
       Cloning https://github.com/IBM-Swift/Kitura-TemplateEngine.git
       Resolving https://github.com/IBM-Swift/Kitura-TemplateEngine.git at 1.6.0
-----> Additional packages to download: libcurl4-openssl-dev openssl libssl-dev
-----> libcurl4-openssl-dev is already installed.
-----> No additional packages to download.
-----> openssl is already installed.
-----> Installing system level dependencies...
-----> Building Package...
-----> libssl-dev is already installed.
-----> Skipping installation of App Management (debug)
-----> Build config: release
       Compile Swift Module 'LoggerAPI' (1 sources)
       Compile Swift Module 'KituraTemplateEngine' (1 sources)
       Compile Swift Module 'Socket' (3 sources)
       Compile Swift Module 'SwiftyJSON' (2 sources)
       Compile Swift Module 'Configuration' (6 sources)
       Compile Swift Module 'HeliumLogger' (2 sources)
       Compile Swift Module 'TestProgram' (1 sources)
       Compile Swift Module 'CloudFoundryEnv' (6 sources)
       Linking ./.build/release/TestProgram
       Compile Swift Module 'SSLService' (1 sources)
       Compile Swift Module 'AmazonConfig' (1 sources)
       Compile Swift Module 'CloudFoundryConfig' (2 sources)
       Compile Swift Module 'HerokuConfig' (1 sources)
       Compile CHTTPParser utils.c
       Compile CHTTPParser http_parser.c
       Linking CHTTPParser
       Compile Swift Module 'KituraNet' (34 sources)
       Compile Swift Module 'Kitura' (43 sources)
       Compile Swift Module 'CloudFoundryDeploymentTracker' (1 sources)
       Compile Swift Module 'Kitura_Starter' (2 sources)
       Linking ./.build/release/Kitura-Starter
-----> Copying dynamic libraries
-----> Copying binaries to 'bin'
-----> Cleaning up build files
-----> Saving cache (default):
-----> - Packages (nothing to cache)
-----> Optimizing contents of cache folder...
-----> Clearing previous swift cache
No start command specified by buildpack or via Procfile.
App will not start unless a command is provided at runtime.
Uploading droplet...
Exit status 0
Staging complete
Uploading droplet, build artifacts cache...
Uploading build artifacts cache...
Uploaded build artifacts cache (929B)
Uploading complete
Uploaded droplet (71.3M)
Destroying container
Successfully destroyed container

1 of 1 instances running

App started


OK

App Kitura-Starter was started using this command `Kitura-Starter`

Showing health and status for app Kitura-Starter in org roliv@us.ibm.com / space dev as roliv@us.ibm.com...
OK

requested state: started
instances: 1/1
usage: 256M x 1 instances
urls: kitura-starter-unsanctified-intervalometer.mybluemix.net
last uploaded: Tue Mar 7 14:53:59 UTC 2017
stack: cflinuxfs2
buildpack: swift_buildpack

     state     since                    cpu    memory      disk      details
#0   running   2017-03-07 08:58:10 AM   0.0%   0 of 256M   0 of 1G
```

Once the application is pushed to and running on Bluemix, you can access your application route to see the welcome page for the Kitura-Starter app. You can log on to your [Bluemix account](https://console.ng.bluemix.net) to find the route of your application or you can inspect the output from the execution of the `cf push` command.  The string value (e.g. Kitura-Starter-unfiducial-flab.eu-gb.mybluemix.net) shown next to the urls should contain the route.  Use that route as the URL to access the sample server using the browser of your choice.

## Kitura Wiki
Feel free to visit Kitura's [Wiki](https://github.com/IBM-Swift/Kitura/wiki) for our roadmap and tutorials.

## Privacy Notice
This Swift application includes code to track deployments to [IBM Bluemix](https://www.bluemix.net/) and other Cloud Foundry platforms. The following information is sent to a [Deployment Tracker](https://github.com/IBM-Bluemix/cf-deployment-tracker-service) service on each deployment:

* Swift project code version (if provided)
* Swift project repository URL
* Application Name (`application_name`)
* Space ID (`space_id`)
* Application Version (`application_version`)
* Application URIs (`application_uris`)
* Labels of bound services
* Number of instances for each bound service and associated plan information

This data is collected from the parameters of the `CloudFoundryDeploymentTracker`, the `VCAP_APPLICATION` and `VCAP_SERVICES` environment variables in IBM Bluemix and other Cloud Foundry platforms. This data is used by IBM to track metrics around deployments of sample applications to IBM Bluemix to measure the usefulness of our examples, so that we can continuously improve the content we offer to you. Only deployments of sample applications that include code to ping the Deployment Tracker service will be tracked.

### Disabling Deployment Tracking
Deployment tracking can be disabled by removing the following line from `main.swift`:

    CloudFoundryDeploymentTracker(repositoryURL: "https://github.com/IBM-Bluemix/Kitura-Starter.git", codeVersion: nil).track()

## Running the application in an IBM Container on Bluemix
This starter application can also be run in an IBM Container in Bluemix. The `ibmcom/kitura-ubuntu` Docker image extends the [swift-ubuntu-docker](https://github.com/IBM-Swift/swift-ubuntu-docker) image. Hence, the `ibmcom/kitura-ubuntu` image also uses Ubuntu v14.04 LTS. For details on how to create an IBM Container to execute a Swift application, please see [10 Steps To Running a Swift App in an IBM Container] (https://developer.ibm.com/swift/2016/02/22/10-steps-to-running-a-swift-app-in-an-ibm-container) and [Running Kitura in an IBM Container](https://developer.ibm.com/swift/2016/03/04/running-kitura-in-an-ibm-container/).

## License
The Kitura-Starter sample app is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE).
