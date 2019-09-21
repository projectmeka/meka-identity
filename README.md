## meka-identity

meka identity is a solution for cross-chain identity based on bip-44. It's to create binding relationship between user's bip44 addresses.

for example, the default polkadot's derive path is `m/44'/359'/0'/0/0` and the default bitcoin derive path is `m/44'/0'/0'/0/0`.

the user can derive many polkadot's addresses and bitcoin's addresses from the same seed. so there is no need to prove if they belongs to the same owner. 

* if the seed is `A`
* the xpub key of bitcoin which is derived from the seed accroding to the path `m/44'/0'` is `B`
* the xpub key of polkadot which is derived from the seed accroding to the path `m/44'/359'` is `C`
* on substrate-based blockchain, send a meesage from `C` address and includes a signed data from `B` to set up the binding relationship.
* bind relationship setup

### future usages
the binding relationship can be used in many ways 
* build bridges
* calc cross-chain reputation
* trace cross-chain portfolio 
* etc...

for the bridge, different from chainx, the meka identity based bridge does not need you to add extre data on btc chain. 

### api

* bind(accountId, chain, xpub, startDate)
* unbind(accountId, chain, xpub, endDate)
* setAdmin(accountId)
* adminBind(accountId, chain, xpub)
* adminUnbind(accountId, chain, xpub)

### storage
* binded(accountId, chain, xpub)[]
* adminAccountId

### pending problems
* is it secure enough to expose the xpub key
* how to strikly prove it's derived from the same seed and if it's necessary
* handle gap easily
