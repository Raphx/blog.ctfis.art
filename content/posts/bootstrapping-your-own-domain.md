---
title: "Bootstrapping your own domain"
date: 2021-07-09T20:25:48+08:00
---
Bootstrapping in this context means, registering for a domain using an email address, and then changing that email address to the one that belongs to the domain itself afterwards. Example, you use `personal@mail.com` to register for `example.com` domain. Once the domain is up, you provision an `admin@example.com` email address, and switch the email for the domain, and DNS hosting service account, to use `admin@example.com`, in place of the personal email address that you used initially.

The reason for doing this is to ensure critical infrastructure is not tied to any personnel. This is helpful, especially for an enterprise or business organisation, as people shift between roles, on-board, and off-board from time to time. Hence, we want to tie these critical infrastructure to a non-changing identity that belongs to the domain itself.

There are 2 major components in bootstrapping a domain and its infrastructure:

  1. The domain name itself.
  1. An email system.

There are providers and vendors in the market who provide end-to-end solution to set up everything on one single platform. But for those who prefer to have more flexibility in managing the domain and email system separately, this post could help you.

Before getting started, make sure you have an email address from a third-party provider, e.g. Microsoft Outlook, Gmail, Yandex, Yahoo, etc. Most providers that offer DNS hosting service or email service require an existing email address to verify your identity. I'll be referring to this type of email addresses as _managed_ email addresses from here onwards.

There are 3 general steps:

  1. Using a managed email address, register for the domain via a DNS hosting service provider (NameSilo, Cloudflare, Google Domains, Amazon Route53, etc.).
  1. Using a managed email address, register for an email service (Protonmail, Migadu, Purelymail, etc.). After you have an email service, add the relevant SPF, DKIM, and DMARC DNS records to your registered domain.
  1. Now you can create a mailbox for your domain's administrator user on your email service. Go ahead and create one. Then, change the managed email address for both accounts on the DNS hosting and email service provider to this new email address, and that completes the entire bootstrapping process. Note that this creates circular dependencies between the services and potential lockout scenarios, but still, I prefer having the domain to not be tied to any managed email address from third-party provider. Ensure there is an account recovery mechanism in place on both systems to avoid being locked out.

Depending on your DNS hosting service provider, some might not allow you to change your email address, or you are using the same personal account to manage other domains, in this case you could create a separate account on the provider using the new administrator email address, and transfer the domain to this new account instead.
