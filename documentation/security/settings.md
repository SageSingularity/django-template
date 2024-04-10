# Security: Settings
Because a settings file contains sensitive information, such as the 
database password, you should make every attempt to limit access to 
it.

## File Permissions
For example, change its file permissions so that only you and 
your web server’s user can read it. This is especially important in
a shared-hosting environment.

## Secret Keys
Every effort should be made to avoid exposing secret keys. One method
is using an environment variable to reference the key, then loading
the key into the environment (such as Cloud services) so that the
built application does not contain it.