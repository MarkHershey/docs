# About GPG Keys

## Terminologies

- [PGP (Pretty Good Privacy)](https://en.wikipedia.org/wiki/Pretty_Good_Privacy): The original encryption tool, proprietary or commercial in modern forms.
- [OpenPGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#OpenPGP): The open standard that defines the file formats and operations for encryption, decryption, signing, etc.
- [GPG (GNU Privacy Guard)](https://gnupg.org/): A free and open-source implementation of the OpenPGP standard, fully compatible with other PGP products.

In short, GPG is the open-source, standards-based successor to the original PGP software. They both use the same underlying concepts (public-key cryptography, digital signatures, key management) and are typically cross-compatible when both follow the OpenPGP standard.

References:

- [The Difference Between PGP, OpenPGP, and GnuPG Encryption](https://www.ipswitch.com/blog/the-difference-between-pgp-openpgp-and-gnupg-encryption)

## Install GnuPG 

- Debian/Ubuntu: `sudo apt update && sudo apt install gnupg -y`
- MacOS: `brew install gnupg`
- Windows: [`Download`](https://www.gpg4win.org/)


## Generate a new GPG key

1. Create a configuration file for key generation
    ```bash
    cat > key.config << EOF
    Key-Type: EDDSA
    Key-Curve: Ed25519
    Key-Usage: sign
    Subkey-Type: ECDH
    Subkey-Curve: Curve25519
    Subkey-Usage: encrypt
    Name-Real: Your Name
    Name-Email: your.email@example.com
    Expire-Date: 0
    %commit
    EOF
    ```
    > Above configuration specifies `Ed25519` for the primary key (for signing) and `Curve25519` for the subkey (for encryption).
    > 
    > `%no-protection` can be added above `%commit` to skip the passphrase protection.
2. Generate the key
    ```bash
    gpg --batch --gen-key key.config
    ```
3. Check the key
    ```bash
    gpg --list-secret-keys --keyid-format=long
    ```


References:

- [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
- [Telling Git about your signing key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
- [Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)


## Export Your Public Key

```bash
gpg --armor --export KEY_ID_HERE > my_public_key.asc
```

## Import Other's Public Key

```bash
gpg --import KEY_FILE_HERE
```

## Complete Backup and Transfer Your GPG Keys

???+ warning

    This section is for backup and transfer all of your GPG keys, which includes all your own key pairs (both private and public) and imported (public) keys if any.

### Export on Original Computer

1. Export your private key (includes your subkeys and public keys)
    ```bash
    gpg --armor --export-secret-keys your.email@example.com > private.gpg
    ```

2. Export entire public keyring (includes all imported keys)
    ```bash
    gpg --armor --export > all_public_keys.gpg
    ```

3. Export trust database
    ```bash
    gpg --export-ownertrust > trust.txt
    ```

4. Create a secure archive
    ```bash
    tar -czf gpg-complete-backup.tar.gz private.gpg all_public_keys.gpg trust.txt
    export GPG_TTY=$(tty) # if headless, this is required
    gpg -c gpg-complete-backup.tar.gz  # Encrypt the archive with a passphrase
    ```

5. Securely delete the unencrypted files
    ```bash
    shred -u private.gpg all_public_keys.gpg trust.txt gpg-complete-backup.tar.gz
    ```

    > `shred` can be installed on MacOS via `brew install coreutils`

### Import on New Computer

1. Decrypt the backup
    ```bash
    export GPG_TTY=$(tty) # if headless, this is required
    gpg -d gpg-complete-backup.tar.gz.gpg > gpg-complete-backup-decrypted.tar.gz
    tar xzf gpg-complete-backup-decrypted.tar.gz
    ```

2. Import your private key (this automatically imports your public key too)
    ```bash
    gpg --import private.gpg
    ```

3. Import all public keys
    ```bash
    gpg --import all_public_keys.gpg
    ```

4. Import trust database
    ```bash
    gpg --import-ownertrust trust.txt
    ```

5. Verify the setup
    ```bash
    gpg --list-secret-keys
    gpg --list-keys 
    ```

6. Clean up
    ```bash
    shred -u private.gpg all_public_keys.gpg trust.txt gpg-complete-backup-decrypted.tar.gz
    ```

References:

- [Killeroid's Gist](https://gist.github.com/Killeroid/6361944d0694e474fb94cc42a3b119d1)
- [Edit trust level manually](https://unix.stackexchange.com/a/407070)
- [GNUPG2 import error](https://superuser.com/a/1327486)


## Delete a GPG key

### Check existing keys

```bash
# check all public keys
gpg --list-keys

# check my secret keys
gpg --list-secret-keys
```

### Delete a key

```bash
# delete a public key
gpg --delete-key KEY_ID_HERE

# delete a secret key
gpg --delete-secret-key KEY_ID_HERE
```

## Manage Multiple GPG Keys

References:

- [How to manage GPG keys across multiple systems?](https://superuser.com/a/466417)
- [How many OpenPGP keys should I make?](https://security.stackexchange.com/a/29858)
- [What is the best way to manage gpg keys across multiple devices?](https://security.stackexchange.com/a/59083)
- [Should I create separate GPG key pairs or just one GPG key pair for multiple uses (e.g. email, sign commits)?](https://superuser.com/a/1683800)