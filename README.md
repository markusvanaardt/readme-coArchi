# About this document
A newbie's guide to configuring source control for Archi using coArchi.

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

![coArchi-manage-plugins](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/8db50362-9750-475d-b769-36405db354d6)

![coArchi-manage-plugins-window](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/d3926b3f-1c90-4753-9ff7-48412012e3d3)

Click [**Install New ...**] and select the downloaded plug-in file.  You may need to restart Archi to activate the plug-in.  Please ensure the plug-in version supports the installed version of Archi.

If your plug-in installation was successful, the [**Collaboration**] menu item will appear on the application menu after restarting Archi.

![coArchi-collaborate](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/f0d14202-ae41-451d-8fd7-0e611f824d43)


# Preparing your Github account to configure Archi integration

To configure Archi for Github integration you would need to create a Personal Access Token (PAT) from your user account.  For a detailed overview of the process you can visit https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

Alternatively, you can follow the steps below:

## Create a Github Personal Access Token (PAT)

1. Log onto your Github account
2. Select [**Settings**] from your account menu (look for the avatar at the right-top of the page)
3. Select [**Developer settings**] from the menu on the left-hand of the page
4. Select [**Personal access tokens**] and then [**Tokens (classic)**]
5. Select [**Generate new token**] and then [**Generate new token (classic)**]

![coArchi-generate-pat](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/8690bd75-8e0e-411e-a782-ec4f767a8e28)

6. Enter your token name, set the token expiry and select the [**repo**] scope for the token
7. Click [**Generate token**]
8. Copy the token from the screen and store it securely for configuration purposes.  **IMPORTANT**: YOU CANNOT RETRIEVE THE TOKEN AFTER IT HAS BEEN GENERATED AND DISPLAYED ON THIS PAGE.  IF YOU LOOSE IT YOU WILL NEED TO GENERATE A NEW TOKEN.

![coArchi-personal-access-token](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/9592e5a7-7242-4165-b440-25730870d818)


## Import the model into Archi from Github

Once you have configured Archi and coArchi, and generated your PAT you will be able to import the Archimate model into the modeller.

From the Collaboration menu, select [**Import Remote Model to Workspace**].  You may need to provide Archi a master password to unlock this feature.

![coArchi-add-remote-model](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/0a43d30f-8fe4-4254-aeda-c926169aef06)

In the **Add Remote Model** modal, provide the following information:

| Field       | Description |
| ----------- | ----------- |
| URL         | The full web URL of the repo: https://github.com/username/reponame.git |
| User Name   | Your Github user name |
| Password    | The PAT you generated earlier |

It is possible that you could use your credentials as-is in the screen.  However, it is recommended that you enable 2FA on your Github account to protect access to the repo.  In this case you will only be able to log onto Github from Archi using the PAT.

To obtain the repo URL, you can copy of from the **Clone** address:

![coArchi-clone](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/80f0db2f-10f8-4f16-b265-7c6d0d95efb6)

## Navigating the UI

From the **Collaboration** menu, select [**Toggle Collaboration Workspace**] and [**Toggle Branches View**].  The Workspace and Branch windows will be docked within Archi.  Archi/coArchi supports repository branches.

![coArchi-navigate-ui](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/1550ed83-1d36-44ce-a758-cf5d0ea40922)


The Collaboration Workspace is used to navigate between different models and individual branches checked out while the Branches View provide the ability to manipulate branches within the selected model. 

## Refresh model

It is recommended to refresh the model from Github prior to making any changes.  Regular refreshes also help to keep local repo copies updated with changes made to the upstream repository.  **It is important to refresh the model prior to committing any changes to avoid overwriting upstream changes made since the local repo copy was pulled from the server**.

To refresh your local copy of the model, open the model / branch from the Collaboration Workspace and select [**Refresh Model**] from the [**Collaboration**] application menu.

## Branching

To protect the integrity of the main branch and avoid overwriting updates from oneanother, it is recommended to create a branch for each piece of work.  Branches could be named by initials, date or subdomain.  Branches can be created either through the coArchi plugin or online on Github.

![coArchi-add-branch](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/a817ba35-8eb2-4a92-a329-a86f1a277dc1)

[**Add branch**] will create a local branch while [**Add branch and checkout**] will create the local branch and set it as the active branch.  Neither of these actions will create the upstream branch (on Github server).

![coArchi-switch-branch](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/d768bc12-39ca-4897-8f75-0b29ab939f57)

## Committing changes

By committing changes you create a local snapshot of the repository into a single package.  **This does not upload the changes to the upstream branch, but create a local packaged copy**.  To commit your latest changes, select [**Commit changes**] from the Collaboration menu.

![coArchi-commit](https://github.com/markusvanaardt/readme-coArchi/assets/17509273/f6df32b7-b664-48b6-8bde-573f9d227b8b)

## Publishing changes

The final step is to publish the committed package back to the repository.  This will insert the last committed package into the upstream branch.

## Merge

On regular intervals all committed and published branches need to be merged into the main branch which will trickle down into all subsequent branches.

# Further reading

For more information on the mechanics and command line (CLI) operations, you can read the following documents:

https://docs.github.com/en/get-started/using-git/about-git

https://git-scm.com/docs/gittutorial

