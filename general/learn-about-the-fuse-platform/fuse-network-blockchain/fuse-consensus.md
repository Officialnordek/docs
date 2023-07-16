# Nordek Consensus

Consensus refers to the agreement process between nodes in a network. The nodes must agree on which transactions to include in the next block on the chain before these transactions are committed.

There are 2 aspects to the process - the actual consensus mechanism to add transactions to blocks, and Sybil protection and validator incentives.

### Sybil protection and incentives via delegated proof of stake

Nordek uses delegated Proof of Stake (dPoS) to provide Sybil protection and align the validator incentives.

To participate in securing the network consensus, a node operator must stake a minimum required amount of NRK tokens (currently set at 100,000 NRK). Becoming a validator on Nordek is permissionless, as long as the node operator meets specific technical requirements. The requirement to stake NRK tokens ensures that an entity cannot create multiple seemingly distinct validators without incurring a significant cost, thus providing Sybil protection. Currently, Nordek allows a maximum of 100 validators.

The validator who successfully publishes a block agreed upon during a consensus round is rewarded by the network protocol with newly minted NRK tokens. Additionally, they receive the transaction fees paid by users for the transactions included in the block.

Over time, validators can expect to publish a share of blocks proportional to their overall stake. Validators can increase their share by attracting NRK tokens from delegators. The delegation mechanics on NRK are discussed in more detail in the [following page](https://docs.nordekscan.com/general/nordek-network-blockchain/validators-and-delegation).

Validators who violate the consensus rules, such as by not revealing random numbers, can expect their stake (including the contributions from delegators) to be frozen. This creates a strong incentive for validators to behave according to the desired rules.

### The AuRa Consensus Model

Currently, Nordek employs Parity's AuRa (Authority Round) [consensus model](https://openethereum.github.io/Aura) to append blocks. This consensus mechanism is also used by the xDAI blockchain.

In the AuRa model, validators take turns signing blocks. Once a block is signed, it is broadcasted to all validators, and if the majority agrees that it is valid, it is added to the blockchain. A new block is added every 5 seconds, regardless of whether any transactions occurred during that time.

While achieving transaction finality in this model may theoretically take some time, for practical purposes, a transaction on Nordek can be considered finalized after a single block confirmation.
