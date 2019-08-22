## Notes

This is known as **Resource Owner Password Credentials Grant (Direct Grants)**. This is used by **REST clients** that want to obtain a token on behalf of a user. 

It is one HTTP POST request that contains the credentials of the user as well as the id of the client and the client’s secret (if it is a confidential client). The user’s credentials are sent within form parameters. The HTTP response contains identity, access, and refresh tokens.
