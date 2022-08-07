---
title: KeeWeb an opensource password manager
date: 2022-08-02 11:00:00 +0200
categories: [application, password manager]
tags: [security, privacy, password]     # TAG names should always be lowercase
---

In today’s days society everyone has more than a couple of online and offline accounts. Most people reuse or only slightly alter their passwords between each account. However, this is a serious security risk. If one password gets compromised, due to the provider not having adequate security measures, your other accounts are automatically at risk. This is only one example of how your login credentials could be compromised.

KeeWeb is a free and open-source password manager compatible with KeePass, available as a web version and desktop apps, for Linux, Windows and Apple. Here you can store your passwords secure notes, like backup codes and files like private keys.

## **Dependencies**

For everything to work out you will need to make sure that you have the following requirements:

* A Linux, Windows or OSX based OS


## **Install KeeWeb**

Navigate to the [KeeWeb website](https://keeweb.info/) and download your the desktop client and install it.


## **Create a database**

Start your KeeWeb application and press the `+ New` button to create your first password database.

![keeweb setup](/assets/img/keeweb/keeweb-setup-1.png){: .shadow w="500" h="200" }

## **Initial database configuration**

Before we can start adding anything we need to make a few adjustments to the database and the application. Don't worry, we only need to do this one.

Navigate to the lock symbol with the name `New`, in the bottom left corner of the window and click on it.

![keeweb setup](/assets/img/keeweb/keeweb-setup-2.png){: .shadow w="500" h="200" }

Under the **Settings** title you will need to add your `Master password` for your password database and confirm it in the field `Confirm Master password`. Here you can also give your database a name via the `Names` field, found under the title **Names**. In my case I named it `My Password Vault`.

> It is recommended to use a password with at least 12 characters. It should include upper and lowercase letters, numbers as well as symbols. It can be a combination of several words / passwords.
{: .prompt-tip }

![keeweb setup](/assets/img/keeweb/keeweb-setup-3.png){: .shadow w="500" h="200" }

When scrolling a bit further down you can enable `Backup this file`. I recommend using the `File` option and selecting a external mount, like Google Drive, OneDrive, Dropbox and so on, by defining the `Backup path:` to point to that external mount.

*Google Drive example (using Google Drive desktop app):* <br>
`G:\My Drive\Backups\Keeweb\My Password Vault.{date}.bak`

![keeweb setup](/assets/img/keeweb/keeweb-setup-4c.png){: .shadow w="500" h="200" }

**History:**
- History size, total MB per file: `32`

**Advanced:**
- Memory, KB: `512000`
- Paralleism: `4`

![keeweb setup](/assets/img/keeweb/keeweb-setup-5c.png){: .shadow w="500" h="200" }

After we have made all these changes we can now save the password database for the first time by clicking the `Save to ...` button. I recommend saving to `File` first. You can always move / upload it to somewhere afterwards.

> Moving the `.kdbx` file while the KeeWeb is open is not recommended. Close / logout of the application first, then move the file to your desired location. After completion you can start / login to your password database by selecting the lock icon `Open` and selecting the `.kdbx` file in its new location.
{: .prompt-warning }

![keeweb setup](/assets/img/keeweb/keeweb-setup-6c.png){: .shadow w="500" h="200" }


## **Initial application configuration**

Like mentioned above we still need to make some ajustments on the core application itself. These can be found under the `General` tab.

**Funktion:**
- Automaticlly save and sync periodically: `On every change`
- Clear clipboard after copy: `In a minute`
- Minimize the app instead of close: `True`

**Audit:**
- Check passwords using an online service Have I Been Pwned: `True` (Optional)

**Auto lock:**
- If the app is inactive: `In 30 minutes`
- When the app is minimized:** `False`
- On password copy: `False`
- On auto-type: `False`
- When the computer is locked or put to sleep: `True`

![keeweb setup](/assets/img/keeweb/keeweb-setup-7.png){: .shadow w="500" h="200" }

<br>

## **Links**

⚙️ If you see something that needs to be fixed, this documentation is open source! Feel free to open an issue [here](https://github.com/r3dspace/r3dspace.github.io).

⭐ If you enjoied the post I would appreciate a star on [GitHub](https://github.com/r3dspace)