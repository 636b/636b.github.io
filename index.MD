# Verifying Signatures

## How to Obtain the Signing Key

Everything posted on this site will be signed with a signature. There are two
ways of verifying the signature. Either download the signing key directly from
<https://636b.xyz/keys/636b-xyz-signing-key.asc>
along with its digests file
<https://636b.xyz/keys/636b-xyz-signing-key.DIGESTS>
or obtain the key from a key-server.

To obtain the signing key directly from the site, issue the following commands:

```console
$ curl -O https://636b.xyz/keys/636b-xyz-signing-key.asc
$ curl -O https://636b.xyz/keys/636b-xyz-signing-key.asc.DIGESTS
$ md5sum -c ./636b-xyz-signing-key.asc.DIGESTS
$ sha1sum -c ./636b-xyz-signing-key.asc.DIGESTS
$ sha256sum -c ./636b-xyz-signing-key.asc.DIGESTS
$ sha512sum -c ./636b-xyz-signing-key.asc.DIGESTS
```

To obtain the signing key from a key-server, issue the following command:

```console
$ gpg --keyserver pool.sks-keyservers.net --recv-keys 0x276ab006abc16a30549ccdf33b0594901a24b9ac
```

Ideally, you may combine the two ways to make sure (at your own discretion).

## Signing Key Fingerprint

Make sure that the key you downloaded has the following fingerprint:

```
pub   rsa2048 2018-07-12 [SC] [expires: 2020-07-11]
      276A B006 ABC1 6A30 549C  CDF3 3B05 9490 1A24 B9AC
uid                  x63x6b <41169869+636b-xyz@users.noreply.github.com>
sub   rsa2048 2018-07-12 [E] [expires: 2020-07-11]
```

Now you may, if you wish, trust the signing key.

## Verifying the Signature

Say you have a file `signed_file` and you wish to verify its signature.
The signature itself is detached and you will need to download
`signed_file.asc` which is located at the same directory as the original
file.

To verify the signature, simply issue the following command:

```console
$ gpg --verify signed_file.asc signed_file
```

