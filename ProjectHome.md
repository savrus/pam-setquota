PAM module to specify user's disk quota when session begins.  This allows users to be present in central dynamic database. To have different policies, pam\_setquota works only with uids from startuid to enduid. If you do not have max uid for the policy, set enduid to 0.
The fs parameter should be either block device or mount point. If fs is not set, homedir filesystem will be used to set quota.

Here are sample PAM config lines:

> session    required     /lib/security/pam\_setquota.so bsoftlimit=19000 bhardlimit=20000 isoftlimit=3000 ihardlimit=4000 startuid=1000 enduid=2000 fs=/dev/sda1

> session    required     /lib/security/pam\_setquota.so bsoftlimit=1000 bhardlimit=2000 isoftlimit=1000 ihardlimit=2000 startuid=2001 enduid=0 fs=/home


This was originally created for a public ssh server at Moscow State University dorms.