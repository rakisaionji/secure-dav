# Secure WebDAV Server

Start a preconfigured WebDAV server (based on [webdav-server](https://www.npmjs.com/package/webdav-server)), which store files in a folder, encrypt and compress them. The encryption is AES256 CBC using a master password.

## Install

```bash
npm i
```

## Usage

```bash
node index.js
```

## Configuration

The default configuration file name is `config.json`.

The string values can refer to another value with the `$(...)` pattern.

Key | Default value | Description
-|-|-
**webdavServerOptions** | `undefined` | Settings of the webdav-server package
**dataFolderPath** | `'.data'` | Folder to store the crypted data
**masterFilePath** | `'data.json'` | File path in which store the resource tree
**masterKeyIteration** | `100000` | Number of hash iteration to get the master key/IV
**fileKeyIteration** | `1000` | Number of hash iteration to get the file-specific key/IV
**keySize** | `32` | Encryption/descryption key size
**ivSize** | `16` | Encryption/descryption IV size
**password** | `'1saw6rar4know8rar'` | Password to use for encryption/decryption
**cipherAlgorithm** | `'aes-256-cbc'` | Algorithm to use for encryption/decryption
**hashAlgorithm** | `'sha256'` | Algorithm to use for the hashes
**multiUser** | `false` | Define if the system must use a multi user system

Here is an example of a configuration file :
```json
{
    "webdavServerOptions": {
        "port": 1900
    },
    "dataFolderPath": "./data/store",
    "masterFilePath": "./data/index"
}
```

## Note

For an unkown reason yet, if you set the *hostname* to `'localhost'` or `'127.0.0.1'`, the Windows embedded WebDAV client will be slower requesting to this server.

## What to do with a WebDAV Server?

You can use it as a virtual repository to store data and allow other softwares to access to it.

For instance (Windows uses `\\localhost@<port>\DavWWWRoot\` to connect to the server ; Linux will need to mount the server or to use a webdav client).
