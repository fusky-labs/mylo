# Mylo DSL

Le cross-languge schema/type generator and transformer, kinda like Prisma but
general purpose for generating types or schema from TypeScript, Python, Go,
Rust, etc.

## Example

The gist is you take this:

```mylo
union Role : string {
  Officer
  Chief
  Mafia
}

schema ZPDCitizen {
  name: string
  nickname: string?
  role: Role | nil
}
```

And you instantly generate to whatever language you prefer to target:

From **Mylo** → **TypeScript**
```ts
type Role = "Officer" | "Chief" | "Mafia"

interface ZPDCitizen {
  name: string
  nickname?: string
  role: Role | null
}
```

From **Mylo** → **Typed Python**
```py
from typing import TypedDict, Optional, NotRequired

Role = Literal["Officer", "Chief", "Mafia"]

class ZPDCitizen(TypedDict):
  name: str
  nickname: NotRequired[str]
  role: Optional[Role]
```


Ideal for generating shared types but is in a different language. Note that it
only generates the infered types and not the actual code itself.

## Contributing

TBA
