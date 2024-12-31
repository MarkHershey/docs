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
    %no-protection
    %commit
    EOF
    ```
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

## Backup and Import your own (private) key

1. List your keys
    ```bash
    gpg --list-secret-keys --keyid-format=long
    ```
2. Export private key (includes all subkeys)
    ```bash
    gpg --export-secret-keys KEY_ID_HERE > private.key
    ```
3. Import the key
    ```bash
    gpg --batch --import private.key
    ```
   - The arg `--batch` is required, here is why: [GNUPG2 import error](https://superuser.com/a/1327486)

4. After importing the key, trusting the key is required:
    ```bash
    gpg --edit-key user@example.com
    ```
   - then, type `trust` and follow the instructions, set the trust level to 5 (ultimate trust) for your own key.
   - Reference: [trust](https://unix.stackexchange.com/a/407070)

This looks like a more comprehensive summary on how to do it properly: [Killeroid's Gist](https://gist.github.com/Killeroid/6361944d0694e474fb94cc42a3b119d1)


## Complete Backup and Import

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
    gpg -c gpg-complete-backup.tar.gz  # Encrypt the archive with a passphrase
    ```

5. Securely delete the unencrypted files
    ```bash
    shred -u private.gpg all_public_keys.gpg trust.txt gpg-complete-backup.tar.gz
    ```

### Import on New Computer

1. Decrypt the backup
    ```bash
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
    gpg --list-secret-keys  # Should show your private keys
    gpg --list-keys        # Should show all public keys
    ```

6. Clean up
    ```bash
    shred -u private.gpg all_public_keys.gpg trust.txt gpg-complete-backup-decrypted.tar.gz
    ```

## Manage Multiple GPG Keys

References:

- [How to manage GPG keys across multiple systems?](https://superuser.com/a/466417)
- [How many OpenPGP keys should I make?](https://security.stackexchange.com/a/29858)
- [What is the best way to manage gpg keys across multiple devices?](https://security.stackexchange.com/a/59083)
- [Should I create separate GPG key pairs or just one GPG key pair for multiple uses (e.g. email, sign commits)?](https://superuser.com/a/1683800)