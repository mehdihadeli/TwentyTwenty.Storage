#20|20 Storage

[![Build status](https://ci.appveyor.com/api/projects/status/0ss5kpj5gy739vwx?svg=true)](https://ci.appveyor.com/project/2020IP/twentytwenty-storage)

### Basic Usage

Initialization:
```
IStorageProvider provider = new AmazonStorageProvider(new AmazonProviderOptions
{
    Bucket = "mybucketname",
    PublicKey = "mypublickey",
    SecretKey = "mysecretkey"
});
```

### Installing User Secrets Manager
The secret manager can be installed globally with:
```
dnu commands install Microsoft.Framework.SecretManager
```

### Adding Project-Specific Secrets
The functional tests depend on access to actual cloud storage provider accounts.  Providing these configuration values can be done through environment variables or the user secret store. Here is how to add settings:

Azure:
```
cd test\TwentyTwenty.Storage.Azure.Test
user-secret set ConnectionString "myreallylongconnectionstring"
```
Amazon:
```
cd test\TwentyTwenty.Storage.Amazon.Test
user-secret set PublicKey "mypublickey"
user-secret set PrivateKey "myprivatekey"
user-secret set Bucket "mybucketname"
```
Secrets can be listed with:
```
cd test\TwentyTwenty.Storage.Azure.Test
user-secret list
```