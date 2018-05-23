# DevOps - Continuous Build,Test and Release of Mobile Foundation Apps and Adapters

Creates a DevOps pipeline for [Mobile Foundation](https://console.bluemix.net/catalog/services/mobile-foundation/). The toolchain creates pipeline for continuous build, deploy, test and release of Mobile Foundation apps and adapters. The pipeline includes the stages for 1)Set up a Mobile Foundation Service on IBM Cloud 2)Build, Deploy and Testing of Adapter 3)Build, Deploy and Testing of Apps 4)Tear Down the Mobile Foundation Service as the last stage.
For Mobile Foundation apps, the pipeline builds the apps with Fastlane, registers the app with Mobile Foundation Server and then tests the app with Appium on Bitbar.
For Mobile Foundation adapters, the pipleline builds the adapters, deploys the adapters to Mobile Foundation Server and tests the adapters.

**Must Read** : In the pipeline stage for building the app (**Build App with Fastlane**), the apps that are built is pushed to a git repo [Publish Apps](https://github.com/ShinojEdakkara/mfp-apps). This git repo can be considered as the private app store, which will be used in the other stages in the pipeline. You need to fork from the above git repo and make sure to modify the environment variables, such as *appPublishUrl*, *gitPushUser*, *gitPushEmail*, *gitPushToken* and *apkGitPushUrl* of the pipeline to be relevant for your forked git repo. The stage uses the access token to push the generated binary (.apk). You need to generate the access token from the github *Settings->Developer Settings->Personal access token*, and use the generated token for *gitPushToken* environment variable. Similarly for **Test App on Bitbar** pipeline stage, modify the *applicationPath* to point to the git repo that you forked above and *bitbarApiKey* with the API Key of the Bitbar instance that you have created in IBM Cloud. The API Key can be found from *API access* section of the *My Account* page of the Bitbar cloud dashboard.

You can create a similar DevOps pipeline for Mobile Foundation BYOL deployments as well as for creating a pipeline with other DevOps tools like Jenkins.

To get started, click **Create toolchain**.

[![Deploy To Bluemix](https://console.bluemix.net/devops/graphics/create_toolchain_button.png)](https://console.bluemix.net/devops/setup/deploy/?repository=https%3A//github.com/ShinojEdakkara/mfp80_toolchain)

For more information about toolchains, see [Custom toolchains in one click with IBM Bluemix DevOps Services](https://developer.ibm.com/devops-services/2016/06/16/open-toolchain-with-ibm-bluemix-devops-services/).
