# Jwk Management

> Every Advantage service call requires a signed JWT assertion, which
means your tool needs an RSA key pair. This guide covers generating
keys, serving 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# JWK Management

Every Advantage service call requires a signed JWT assertion, which
means your tool needs an RSA key pair. This guide covers generating
keys, serving a JWKS endpoint, and rotating keys.

> #### Leaked keys let attackers impersonate your tool {: .warning}
>
> Your private key signs the OAuth assertions that prove your tool's
> identity to platforms. If an attacker obtains it, they can request
> access tokens and call platform APIs as your tool, accessing roster
> data, posting grades, or reading course content. Never commit key
> material to version control, log it, or expose it via API responses.

## Generating a key

```elixir
jwk = Ltix.JWK.generate()
```

Store `private_key_pem` and `kid` in your database or config. To
reconstruct the struct later, pass them to `Ltix.JWK.new/1`.

Use a separate key per registration so you can rotate them
independently.

## Serving a JWKS endpoint

Platforms fetch your public keys to verify your tool's signed
assertions. You provide the JWKS endpoint URL during tool
registration.

Each key has a unique `kid`, so platforms match signatures to the
correct key automatically. Pass your JWKs to `to_jwks/1` and it
returns a JWKS map with only the public halves:

```elixir
Ltix.JWK.to_jwks([jwk_1, jwk_2])
#=> %{"keys" => [%{"kty" => "RSA", "kid" => "...", "n" => "...", ...}, ...]}
```

Private material is stripped automatically.

For tools with a single registration, you can hard-code a single key.
For tools managing multiple registrations, see the
[Managing JWKs with Ecto](cookbooks/managing-jwks-with-ecto.md) cookbook for a
database-backed approach with key rotation.

## Key rotation

When you rotate a key, your JWKS endpoint must continue serving the
old public key until platforms have refreshed their cache. A typical
overlap period is 24-48 hours.

The rotation sequence:

1. Generate a new key
2. Start using the new key for signing
3. Serve both old and new public keys from your JWKS endpoint
4. After the overlap pe

*[truncated — see source for full prompt]*