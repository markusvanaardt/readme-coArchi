# About this document
An idiot's guide to configure coArchi on Archi

# Archimate model, repository and Git integration

The repository contains the Archimate architecture landscape models built using Archi.

Below are detailed instructions on installing and configuring Archimate, the coArchi plugin and integrating with Github.

# Setting up and configuring Archi and the plug-in

## Installing and configuring Git CLI

Request Git CLI installation from your IT support team, or download it from https://gitforwindows.org/

Once installed, it is required that you disable SSL verification due to a limitation of the coArchi plugin.  Make the following configuration changes under C:\Users\[username]\.gitconfig :

```
[https]
	sslVerify = false
[http]
	sslVerify = false
```

## Installing Archi

Download and install the latest version of Archi from https://www.archimatetool.com/download/

## Download and install the coArchi plug-in

From https://www.archimatetool.com/plugins/ download the most recent version of **coArchi**.

To install the plug-in, open Archi and install from the application menu: Help > Manage Plug-ins:

![image](https://user-images.githubusercontent.com/17509273/217602620-2aec1e61-ec7f-4bff-b5a3-42bdc86ff4f7.png)

![image](https://user-images.githubusercontent.com/17509273/217603667-ddff409c-8e9e-4fe1-817a-64386b800b05.png)

Click [**Install New ...**] and select the downloaded plug-in file.  You may need to restart Archi to activate the plug-in.  Please ensure the plug-in version supports the installed version of Archi.

If your plug-in installation was successful, the [**Collaboration**] menu item will appear on the application menu after restarting Archi.

![image](https://user-images.githubusercontent.com/17509273/217616043-a61adbc4-18b1-406f-9177-99803817f117.png)

# Preparing your Github account to configure Archi integration

To configure Archi for Github integration you would need to create a Personal Access Token (PAT) from your user account.  For a detailed overview of the process you can visit https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

Alternatively, you can follow the steps below:

## Create a Github Personal Access Token (PAT)

1. Log onto your Github account
2. Select [**Settings**] from your account menu (look for the avatar at the right-top of the page)
3. Select [**Developer settings**] from the menu on the left-hand of the page
4. Select [**Personal access tokens**] and then [**Tokens (classic)**]
5. Select [**Generate new token**] and then [**Generate new token (classic)**]

![image](https://user-images.githubusercontent.com/17509273/217618727-e1cffefd-eaf2-48c2-bdf7-bc31b6adc75d.png)

6. Enter your token name, set the token expiry and select the [**repo**] scope for the token
7. Click [**Generate token**]
8. Copy the token from the screen and store it securely for configuration purposes.  **IMPORTANT**: YOU CANNOT RETRIEVE THE TOKEN AFTER IT HAS BEEN GENERATED AND DISPLAYED ON THIS PAGE.  IF YOU LOOSE IT YOU WILL NEED TO GENERATE A NEW TOKEN.

![image](https://user-images.githubusercontent.com/17509273/217619619-d1a82044-3abe-45c6-9603-8e00883039cd.png)

## Import the model into Archi from Github

Once you have configured Archi and coArchi, and generated your PAT you will be able to import the Archimate model into the modeller.

From the Collaboration menu, select [**Import Remote Model to Workspace**].  You may need to provide Archi a master password to unlock this feature.

![image](https://user-images.githubusercontent.com/17509273/217621696-31b1382d-c9fb-46fe-9902-cd2b762a893d.png)

In the **Add Remote Model** modal, provide the following information:

| Field       | Description |
| ----------- | ----------- |
| URL         | The full web URL of the repo: https://github.com/username/reponame.git |
| User Name   | Your Github user name |
| Password    | The PAT you generated earlier |

It is possible that you could use your credentials as-is in the screen.  However, it is recommended that you enable 2FA on your Github account to protect access to the repo.  In this case you will only be able to log onto Github from Archi using the PAT.

To obtain the repo URL, you can copy of from the **Clone** address:

![image](https://user-images.githubusercontent.com/17509273/217622267-287f3615-f79a-464e-af2d-e51ee35ba9b1.png)

## Navigating the UI

From the **Collaboration** menu, select [**Toggle Collaboration Workspace**] and [**Toggle Branches View**].  The Workspace and Branch windows will be docked within Archi.  Archi/coArchi supports repository branches.

![image](https://user-images.githubusercontent.com/17509273/217623244-347a6e93-49e8-4849-8fbd-e0d10a12e1d2.png)

The Collaboration Workspace is used to navigate between different models and individual branches checked out while the Branches View provide the ability to manipulate branches within the selected model. 

## Refresh model

It is recommended to refresh the model from Github prior to making any changes.  Regular refreshes also help to keep local repo copies updated with changes made to the upstream repository.  **It is important to refresh the model prior to committing any changes to avoid overwriting upstream changes made since the local repo copy was pulled from the server**.

To refresh your local copy of the model, open the model / branch from the Collaboration Workspace and select [**Refresh Model**] from the [**Collaboration**] application menu.

## Branching

To protect the integrity of the main branch and avoid overwriting updates from oneanother, it is recommended to create a branch for each piece of work.  Branches could be named by initials, date or subdomain.  Branches can be created either through the coArchi plugin or online on Github.

![image](https://user-images.githubusercontent.com/17509273/217628704-308d9051-c61a-4b7a-a71a-b28d42f4dce5.png)

[**Add branch**] will create a local branch while [**Add branch and checkout**] will create the local branch and set it as the active branch.  Neither of these actions will create the upstream branch (on Github server).

![image](https://user-images.githubusercontent.com/17509273/217629681-8016d68b-d048-4c29-b8d2-5a9ca2242905.png)

## Committing changes

By committing changes you create a local snapshot of the repository into a single package.  **This does not upload the changes to the upstream branch, but create a local packaged copy**.  To commit your latest changes, select [**Commit changes**] from the Collaboration menu.

![image](https://user-images.githubusercontent.com/17509273/217631182-30277689-db0d-4727-8fcc-a07aec2c0cf2.png)

![image](https://user-images.githubusercontent.com/17509273/217631691-a0704965-c59c-42ec-a4c0-c7b2ebfa9b01.png)

## Publishing changes

The final step is to publish the committed package back to the repository.  This will insert the last committed package into the upstream branch.

## Merge

On regular intervals all committed and published branches need to be merged into the main branch which will trickle down into all subsequent branches.

# Further reading

For more information on the mechanics and command line (CLI) operations, you can read the following documents:

https://docs.github.com/en/get-started/using-git/about-git

https://git-scm.com/docs/gittutorial

