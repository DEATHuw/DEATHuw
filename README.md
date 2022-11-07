curl -X POST -H "Authorization: Bot $TOKEN" -H "Content-Type: application/json" \
  -d '{
    "type":1,
    "name":"command",
    "description":"description",
    "guild_id":"$GUILD_ID",
    "options":[
      {
        "type":1,
        "name":"subcommand",
        "description":".",
        "options":[
          {
            "type":3,
            "name":"not-required",
            "description":"."
          },
          {
            "type":3,
            "name":"required",
            "description":".",
            "required":true
          }
        ]
      }
    ]
  }' https://discord.com/api/v10/applications/$APPLICATION_ID/guilds/$GUILD_ID/commands
Expected Behavior
This error to be returned:

{"code": 50035, "errors": {"options": {"1": {"_errors": [{"code": "APPLICATION_COMMAND_OPTIONS_REQUIRED_INVALID", "message": "Required options must be placed before non-required options"}]}}}, "message": "Invalid Form Body"}
Current Behavior
{"message": "500: Internal Server Error", "code": 0}
Screenshots/Videos
No response

Client and System Information
curl 7.85.0 (x86_64-pc-linux-gnu) libcurl/7.85.0 OpenSSL/3.0.5 zlib/1.2.11 brotli/1.0.9 zstd/1.5.2 libidn2/2.3.3 libpsl/0.21.0 (+libidn2/2.3.2) libssh/0.9.6/openssl/zlib nghttp2/1.49.0 librtmp/2.3

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.10
DISTRIB_CODENAME=kinetic
DISTRIB_DESCRIPTION="Ubuntu 22.10"
