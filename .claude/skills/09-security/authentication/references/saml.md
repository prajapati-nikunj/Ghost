# SAML Reference

## Overview
SAML (Security Assertion Markup Language) is used for enterprise SSO (Single Sign-On).

## Flow
1. User accesses Service Provider (SP).
2. SP redirects to Identity Provider (IdP) with SAML AuthnRequest.
3. IdP authenticates user.
4. IdP sends SAML Response (assertion) back to SP.
5. SP validates assertion and creates session.

## When to Use
- Enterprise B2B applications requiring SSO.
- Integration with corporate identity providers (Okta, Azure AD, OneLogin).
- Compliance requirements (SOC 2, HIPAA).

## Note
For most consumer applications, prefer **OAuth 2.0 / OIDC** over SAML.
