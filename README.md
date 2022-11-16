# Vue, Nhost, and Security keys

1. install the dependencies

```sh
pnpm i
```

2. Run the Nhost CLI

```sh
nhost dev --no-browser
```

3. On a separate terminal, start the web app:

```sh
pnpm dev
```

4. Browse to `http://localhost:5173/`, **not 127.0.0.1** as WebAuthn requires the `localhost` origin

## How it's configured in `nhost/config.yaml`

```yaml
auth:
  webauthn:
    enabled: true
    rp_name: Example App # In the cloud, this is the application name
  client_url: http://localhost:5173 # The frontend url. Required by Webauthn
  email:
    signin_email_verified_required: false # Authenticate straight after adding the security key, instead of having to click on the verification email
```
