# Adding a public SSH key to an eCloud Flex instance

If you would like a UKFast support engineer to troubleshoot issues on your eCloud Flex instance, you'll need to add a public SSH key and grant access to `ukfastsupport`.  Once you've [requested an SSH key via MyUKFast](/cloud/flex/support/requestsshkey.html), follow the steps below to add this to your instance.

Either login to the instance as root user, or prefix all commands with `sudo`:

1. Create the `ukfastsupport` user:
```
useradd -m -s /bin/bash -G wheel ukfastsupport
```
(For Debian/Ubuntu, replace `wheel` with `sudo`)


2. Switch to the ukfastsupport user:
```
sudo -u ukfastsupport -i
```

3. Create the `.ssh` directory if it doesn't exist:
```
mkdir /home/ukfastsupport/.ssh
```

4. Edit the authorized_keys file:
```
nano /home/ukfastsupport/.ssh/authorized_keys
```

5. Paste the key into the file ensuring that it's entirely on a single line. Save the file with CTRL+O <ENTER> then exit with CTRL+X.

6. Ensure the permissions on the files are set correctly - this must be done or SSH will deny access:
```
chown -R ukfastsupport:ukfastsupport /home/ukfastsupport/.ssh
chmod -R u+rwX,og-rwx /home/ukfastsupport/.ssh
```

If you run into any problems on this, please raise a support ticket via [MyUKFast](https://my.ukfast.co.uk/pss/add.php), or call support directly on 0800 230 0032.
