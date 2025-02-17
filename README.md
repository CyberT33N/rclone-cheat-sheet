# rclone-cheat-sheet


# Install
- https://rclone.org/install/

## Ubuntu
```shell
sudo -v ; curl https://rclone.org/install.sh | sudo bash
```

















<br><br>
<br><br>
___
<br><br>
<br><br>



# Cloud Storage

<details><summary>Click to expand..</summary>

# Proton Drive
- https://rclone.org/protondrive/

```shell
rclone config

# Choose n) New remote

# set as name `remote`

# Choose number for Proton Drive - 43 / Proton Drive

# Enter username

# Choose y) Yes type in my own password

# Enter 2fa of your authenticator app

# Select y at Edit advanced config?

# Select y if you choosed a second layer password

# At encoding rpess enter for default

# Press again enter as default for file size

# Press again enter as default for app version

# Choose true for replace_existing_draft

# Choose true for enable_caching

# Set description for your remote

# Then choose no if it ask again for Edit advanced config?
```






<br><br>
<br><br>

# FAQ

## WARN RESTY 422 POST https://mail.proton.me/api/auth/v4: For security reasons, please complete CAPTCHA. If you can't pass it, please try updating your app or contact us here: https://proton.me/support/appeal-abuse (Code=9001, Status=422), Attempt 1
2025/02/17 13:07:41.224555 ERROR RESTY 422 POST https://mail.proton.me/api/auth/v4: For security reasons, please complete CAPTCHA. I
- Open `https://mail.proton.me` in new incognito browser window, sign-in and solve captcha. Then your host IP will be marked as captcha solved and you can continue

<br><br>

## WARN RESTY 422 POST https://mail.proton.me/api/auth/v4/2fa: Incorrect login credentials. Please try again. (Code=8002, Status=422), Attempt 1
- When youc reate your config and you enter your 2FA then it will will change in meantime so you must set the 2fa via you cli command e.g. in this list file command:
```shell
rclone ls remoteNameHere: --protondrive-2fa=123456
```

  
</details>



