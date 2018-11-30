# Secure by Design
 > the Architect's Guide to Secure Design Principles by Eoin Woods

Security is our protection against malice, mistakes and mischance

It's a risk management model. Balance cost against risk
 - Loss of time, money, privacy and reputation

## Secure Application Design
Applications have not necessarily got less secure, the threat landscape has massively increased

There are many sets of security principles
- Viega and McGraw
- OWASP
- NIST
- NCSC
- Cliff Berg

Many of these have shared fundamentals

### Principles

#### Least Privilege

Ensure services have onlt exactly what they need. Don't provide broad privilege for things

#### Separate Responsibilities
Allows a more fine grained control, and better auditing for access.

Can be hard to massively scale and then manage

#### Trust Cautiously
Lots of issues arise due to trusting bad actors

Always assume unknown entities are untrusted

#### Simplest Solution Pssible
Complex solutions and designs are hard to understand and almost always hard to secure

Remove uneccessary features and implicit behaviour. Can be hard at a product level to understand what to remove and what to add. Break into other easily securable services

#### Audit Sensitive Events
Understanding what happens makes it easier to stop it in the future

Store audit logs separate, append only and locked down

#### Secure Defaults and Fail Securely
Have secure defaults and don't use 'comes out the box' passwords and security access

If you fail or error, don't then expose information

#### Never Rely on Obscurity
> They will never guess that

Except they will. 

There are so many pople looking at your online system that someone will eventually guess it

#### Defence in Depth
don't have one point of security. Secure in layers

MFA is a good example of this. Single points of failures anywhere are bad

Should messages be encrypted across the bus?

#### Never Invent Security Technology
Security is complicated and hard. There are lots of proven and tested protocols and techniques that already exist, so we should use them.

#### Secure the Weakest Link
Keep finding the weakest link, and make it more secure. Then repeat to find the next weakest link, and so on.

The weakest link is only weak based on the threat model