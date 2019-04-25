# TuringCreds concept

## High-level goals

We want to incentivize the full exploration of as much of the Turing space as possible, as well as make it available for use to researchers and engineers. This involves tackling two different incentivization issues:

- The storage and transmission of existing tape outputs upon request.

- The computation of UTM configurations and honest reporting of tape outputs.

## Architectural and Game Theoretic Concerns

Incentivizing the connected goals of the long-term commitment of storing and serving tape outputs and the persistent but short-lived requirement for computing UTMs to either known beaver or halt state are two very different economic requirements. Prior attempts including Sia, Filecoin, Blockstack all have only one requirement: pay for storage. Simply paying for computation and paying for storage is an option, but the connective token(s) would be open to a large field of undesirable incentives for gaming the system, producing false results faster, or in some cases holding the system hostage. The intention of this project is not to provide a revenue-stream for participants, but to compensate for the real costs in electricity and hardware that are part of participation.

In the space of trusted multiparty computing there are several major approaches vying for dominance, typically based off some mix of cryptography, game theoretic incentives and sometimes plain thermodynamics. Proof of Exercise is an ideal candidate for validating participant rewards and enabling their transfer. This is not to be confused with consensus, this is a tool for sybil resistance. For consensus the leading option is Avalanche Consensus, it works well with Proof of Exercise and provides very little overhead. We do not anticipate the users of this system desiring high-throughput transactions or a Turing-complete smart contract platform, this is merely a way to fairly compensate the participants. It makes sense then to build it on the security guarantees of an existing smart-contract platform like Ethereum, Zilliqa or perhaps even Bitcoin using Proof of Proof over a Directed Acyclic Graph of transfers.

In order to tie this unusual architecture to what is presently known about tokenomics, a mutual credit system is proposed to encompass the needs of the system without attempting to balance exchange rates between multiple tokens. This mutual credit system would enable new participants to 'check out' a chunk of the computed UTM space, begin computations and use those outputs to build an anonymous stake. This anonymous stake's purpose is not to reward the new participant, but to grant them access to the network of Avalanche peers which requires something to be staked. This peer, once they have sufficient anonymous results to contribute may submit this bundle as stake for an identity from the network, enabling actual participation. This stake acts as a lens, controlling the rate at which this new identity can grow. Thus users who wish to earn more TuringCreds must continue to stake more TuringCreds, rewarding consistency and true commitment to the platform.

Validated storage is the component that requires the most consideration. The transaction chain will likely be processed by the hosting smart contract platform, obviating the need for a blockchain in this design. Instead a peer to peer storage network will be utilized to store the enumeration, map that enumeration to tape outputs and force every commitment of tape to be tied to both a user and a transaction which serves as compensation. Further confirmations that this tape indeed conforms to the UTM will be required with some probability from existing avalanche stakers and anonymous new participants seeking entrance into the consensus membrane. Thus cheaters must stake against their immutable claim that will likely one day be proven false. The more false claims they stake, the faster their own stake will be slashed. This gives systems architects fewer dials to concern themselves with, because at its heart the optimal required stake does not require an estimate of the odds that the node is byzantine. To ensure proper incentives the required stake need only balance the (incoming new peers + proportion of avalanche peers doing backvalidations) against the permitted output rate in proportion to the stake * the interval before stakes can be withdrawn. Thus ensuring that cheaters never prosper by making it almost certain that cheating is not worth it over the time interval.