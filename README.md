[![hackmd-github-sync-badge](https://hackmd.io/wPTUeTzwQ3q9uXhuKHf3Cg/badge)](https://hackmd.io/wPTUeTzwQ3q9uXhuKHf3Cg)
###### tags: `documentation` `design`

# The Secrets Cockpit

This is a UI which enables free account management using the [Secret Management Style](https://hackmd.io/PZjpRfzPSBCqS-8K54x2jA)

## Account types
As we may associate much better the concept of an account. We will use the word "account" here.
This way a key is for accesssing the account. One specific key will have an id to be externally indentifiable.
Because the key is the essential part to decrypt and have access to whatever the account should be used for - we distinguish the account types in the way how we handle the keys.

1. Unsafe Keys
2. Floating Keys 
3. Signature Keys

The discrimination of those key types is merely for security considerations and important to the Secrets Cockpit for how the keys are generated and if they are allowed to be stored - from the perspective of any secret-management-service no such discrimination exists.

To counter potential confusion about the wordings:

- Key = Seccret Key = Private Key
- Id = Public Key

### Unsafe Keys
These are keys which are generated on the Browser and often stored in LocalStorage.
These are called "unsafe" as everyone having access to your Browser Profile may read the LocalStorage and thus might read these keys.
That means the "Unsafe Keys" are similarily safe like any other kind of Access Token - however they are permanent and would have their associated SecretSpace as any other key.

### Floating Keys
There are keys to never be stored anywhere. They are generated out of a seedphrase provided by the user and the user must rely on their memory for the retrieval.They also should be strong, very strong.
As soon as either the seedphrase or the key is stored somewhere, as same as when the seedphrase is weak - the key should be considered "unsafe" anyways.

Such a key as derived from a strong seedphrase may be used for a Master SecretSpace which is storing other "Unsafe Keys" for mobility.

### Signature Keys
Also these keys are never being stored anywhere. They are derived from a specific or a random string, signed with your Wallet Private Key using MetaMask then hashed.

Also such a key may be used for a Master SecretSpace to store other "Unsafe Keys".
Also you could remember the specific seedphrade for signing and store it on your devices without significant loss of the security properties.

## Aliases
For convenience we have introduced the feature to provide an alias for specific Ids.
A Key has the same unique Id anywhere. On top of that you may speficy any arbitrary human readable String for your Account to easily identify it.

(Key -> Id) -> Alias

Outside of the specific instance  of the Secret Cockpit these aliases are not known.


## Features v0.1

- [x] Define URL to specific secret-manager service to be used
- [x] Section to choose specific input method
- [x] Use input for pasting Unsafe Keys
- [x] Use password input to generate Floating Keys
- [x] Retrieve and inspect SecretSpaces
- [x] Edit Secrets
- [x] Add Secrets
- [x] Delete Secrets
- [x] Add foreign Subspace
- [x] Delete foreign Subspace
- [x] Copy Secrets
- [x] Store Secrets in secretSpace
- [x] Store Unsafe Keys in localStorage
- [x] Store Unsafe Keys in secretSpace
- [x] Store shared Secrets
- [x] Share Secrets
- [x] Use Aliases for Ids
- [x] QR-Code Import
- [x] QR-Code Export
- [x] messagebox for user-feedback
- [x] detect and import stored unsafe keys

## Features v0.2
- [ ] Use MetaMask for Signature Keys
- [ ] Keylogger Protection
- [ ] Data Manager for synchronizing whole local State

## Ideas
- Create Secrets Backup File (connect to data-manager)

