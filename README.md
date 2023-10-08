Bitcoin Core with ordisrespector patch
======================================

For more information on what Bitcoin Core is, please refer to the [reference repository](https://github.com/bitcoin/bitcoin)

what is a inscription ?
-----------------------

Inscriptions are the exploit of embedding arbitrary data in the witness of a transaction using the OP_CODE: `OP_IF`,`OP_FALSE`.

What do they allow?
-------------------

This exploit has been possible since the arrival of SegWit in 2017, at that time the size of a witness was a maximum of 3600 bytes, which would have limited the data included in a inscription, however with the arrival of Taproot the limit has simply been removed, limiting the size of inscription to 4MB (block size).

With the removal of the limit, inscriptions have enough space to carry text, audio, images and even videos.

Why is this not desirable?
--------------------------

Firstly, as inscriptions are directly recorded on the chain, ALL nodes in the network must download this data even if the owner of the node does not wish to have this data.

Secondly, it makes the chain heavier, thus increasing the IDB (initial blockchain download). A bigger chain means more resources to run a node depriving the people with the least means of running a node and validating the consensus.

Thirdly each inscription creates a UTXOs thus increasing the [UTXOs](https://en.bitcoin.it/wiki/UTXO) set that each node must contain even the pruned nodes.

Fourth, illegal data can be added to the chain, potentially exposing nodes runner to legal action.

The total size of inscriptions as well as the UTXOs linked to inscriptions can be consulted on [ordiscan](https://ordiscan.com/).

It is also possible to consult a [mempool](https://github.com/mempool/mempool) [instance](https://orangepill.ovh) empty of inscription.

how to get rid of it?
---------------------

the simplest way (the one used in this fork) is to standardize these transactions, that is to say that the nodes which execute this patch will simply not relay the inscription, this can only work if a very large number of nodes executing the patch (>90%).

where does this patch come from?
--------------------------------

The patch was written by @luke-jr you can see the code alone right here.
@luke-jr is a long-time developer on bitcoin, feel free to consult the code and these previous works to judge its reliability.

And then?
---------

A new patch was also written by @luke-jr and is currently under revision to be merged with Bitcoin Core. You can consult the details and the PR [here](https://github.com/bitcoin/bitcoin/pull/28408).
Once it has been merged, everyone will be able to use this patch without having to go through alternative clients.