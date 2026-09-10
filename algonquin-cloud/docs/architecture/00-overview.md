# AC Cloud Overview

AC Cloud is a shared capability plane, not a monolithic application. Product
systems retain their own APIs, storage, release cycles, and failure boundaries.

```text
clients and product services
            |
       API gateway
            |
 identity | policy | catalog | events
            |
 network | data | messaging | observability | secrets
```

Every dependency must be explicit, authenticated, observable, and replaceable.
