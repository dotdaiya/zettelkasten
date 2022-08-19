# Mail maximum length

Email's maximum lenght is defined and standarized, see t`rfc/inline-errata/rfc3696`. The maximum lenght of a mail is 256:
- 64 characters in the local part
- 1 characters '@'
- 192 characters in the domain part

Technically the maximum length is 320 chars, but as the *rfc* states:
> That limit is a maximum of 64 characters (octets)
> in the "local part" (before the "@") and a maximum of 255 characters
> (octets) in the domain part (after the "@") for a total length of 320
> characters. However, there is a restriction in RFC 2821 on the length of an
> address in MAIL and RCPT commands of 256 characters.  Since addresses
> that do not fit in those fields are not normally useful, the upper
> limit on address lengths should normally be considered to be 256.
