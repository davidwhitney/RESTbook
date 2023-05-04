# Versioning (and Forwards Compatibility)

- Be version infinite.
    - Clients must always be tolerant to additions.
    - Remove depreciated things from docs but leave them in responses.
    - Only hard version breaks remove old things to cleanup

- Media-Type versioning trumps URL versioning
    - Latest by default behaviour

- Deprecating APIs
    - Managed removal of old APIs
    - Long term projects
    - Warning headers for users of depreciated APIs
    - Soft failures with header overrides
    - Eventual deletion
