# Nordek Consensus

Consensus is a fault-tolerant mechanism used in blockchain systems to ensure agreement on the network's single state. The Nordek network utilizes a [Delegated Proof of Stake](https://en.bitcoinwiki.org/wiki/DPoS) (DPoS) consensus model. DPoS is a variation of [Proof of Stake](https://en.bitcoinwiki.org/wiki/Proof-of-stake) consensus.&#x20;

In PoS, a group of validators is responsible for updating and validating the network's state. Validators take turns to update the network, while the other validators verify the validity of the updates.

The Consensus contract manages the list of network validators and delegators.

The BlockReward contract calculates the reward amount that validators and delegators receive for each validated block. The size of the reward is proportional to the validator's stake.

The Voting contract allows validators to vote on various changes related to the three fundamental contracts mentioned above. These contracts are proxied with an implementation that handles the logic. Changes to the implementations can only be made through the Voting process.

The bridge facilitates the transfer of Nordek native tokens between the Nordek and Ethereum networks.

## [Consensus - 0x3014ca10b91cb3d0ad85fef7a3cb95bcac9c0f79](https://nordekscan.com/address/0x3014ca10b91cb3d0ad85fef7a3cb95bcac9c0f79)

This contract manages the DPos consensus of the network. It is responsible for storing the current set of validators and selecting a new validator set at the end of each cycle. The process of updating the validator set involves choosing a random snapshot from the snapshots taken during the cycle.

Snapshots are taken of pending validators, who are individuals that have staked an amount greater than the minimum required to become a network validator. Additionally, this contract handles the functionalities of staking, delegating, and withdrawing funds.

The stake amount for a validator is determined by the sum of the staked amount and the delegated amount associated with its address.

This contract is based on `non-reporting ValidatorSet` [described in Parity Wiki](https://wiki.parity.io/Validator-Set.html#non-reporting-contract).

{% hint style="info" %}
* Minimum stake amount = 100,000 Nordek token
* Cycle duration blocks = 34560 (approximately 2 days)
{% endhint %}

## [Block Reward - 0x7429fB101C317743369f3A161A6Ee78c3Ac45ADd](https://nordekscan.com/address/0x63d4efed2e3da070247bea3073bcab896dff6c9b)

This contract's main purpose is to generate and distribute block rewards to the network validators based on the network specifications, which include a 5% yearly inflation rate.

Additionally, it has the responsibility of invoking the snapshot/cycle logic on the Consensus contract.

It's important to note that this contract is based on the non-reporting `BlockReward` as [described in Parity Wiki](https://wiki.parity.io/Block-Reward-Contract).

## [Voting - 0xC59D39E832316504219B7236Ea03919B9dF96FDD](https://nordekscan.com/address/0xC59D39E832316504219B7236Ea03919B9dF96FDD)

The primary function of this contract is to facilitate the opening of new ballots and enable voting to accept or reject proposed changes to other network contracts' implementations. Ballots essentially serve as proposals for modifying existing contracts.&#x20;

Only network validators have the authority to initiate new ballots, while anyone can participate in voting. However, it's important to note that only the votes from validators are considered when determining the outcome of a closed ballot.&#x20;

The opening and closing of ballots occur at the end of each cycle.

{% hint style="info" %}
* Max number of open ballots = 100
* Max number of open ballots per validator = 100 / number of validators
* Minimum ballot duration (cycles) = 2
* Maximum ballot duration (cycles) = 14
{% endhint %}

## [Proxy Storage](https://nordekscan.com/address/0x23D8634ED1B2662dC96FcE6208fde93258731333)

This contract plays a crucial role in managing the implementation addresses of network contracts and facilitating their upgrades when deemed necessary through a voting process.
