# Using google firebase emulator on an custom local domain
When using a custom local domain for your firebase emulator, it will give an error when using the sign-in popup.

To fix this (for now) change the core..

On OSX:

open  ```/usr/local/lib/node_modules/firebase-tools/lib/emulator/auth/operations.js```

Search for "localhost", there should be something like :

```
function getProjects(state) {
    return {
        projectId: state.projectNumber,
        authorizedDomains: [
            "localhost",
        ],
    };
}
```

change the autorized domain to some domain you use locally

```
function getProjects(state) {
    return {
        projectId: state.projectNumber,
        authorizedDomains: [
            "dev.your-domain.com",
        ],
    };
}
```

Save the file, and voilla! restart or start the emulator and it should work now :-)
