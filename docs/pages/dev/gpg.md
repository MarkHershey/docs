# About GPG Keys

## Terminologies

- [PGP (Pretty Good Privacy)](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)
- [OpenPGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#OpenPGP) Protocol
- [GPG (GNU Privacy Guard)](https://gnupg.org/)

References:

- [The Difference Between PGP, OpenPGP, and GnuPG Encryption](https://www.ipswitch.com/blog/the-difference-between-pgp-openpgp-and-gnupg-encryption)

## Generate a new GPG key

References:

- [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
- [Telling Git about your signing key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
- [Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)

## Export and Import Key

```
gpg --list-secret-keys user@example.com
```

```
gpg --export-secret-keys KEY_ID_HERE > private.key
```

```
gpg --batch --import private.key
```

- [GNUPG2 import error](https://superuser.com/a/1327486)

## Manage Multiple GPG Keys

References:

- [How to manage GPG keys across multiple systems?](https://superuser.com/a/466417)
- [How many OpenPGP keys should I make?](https://security.stackexchange.com/a/29858)
- [What is the best way to manage gpg keys across multiple devices?](https://security.stackexchange.com/a/59083)
- [Should I create separate GPG key pairs or just one GPG key pair for multiple uses (e.g. email, sign commits)?](https://superuser.com/a/1683800)