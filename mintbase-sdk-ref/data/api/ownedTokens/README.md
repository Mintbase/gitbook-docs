# ownedTokens
Returns tokens owned by `ownerId` with limit and offset pagination.
### ownedTokens(ownerId: string, { limit, offset }: Pagination)

Example:

```ts
import { ownedTokens, OwnedTokens } from '@mintbase/data'

const ownedTokens: OwnedTokens[] = ownedTokens('mb_alice.near', { limit: 20 });

console.log(ownedTokens.length) // => 2

```