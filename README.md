# LoopringNftTransferDemoSharp
This is a demo repo to show how to do NFT transfers between accounts on Loopring in C#.

It uses a ***Metamask/Gamestop wallet*** private key to sign the transfers so you will need to export that out from your Metamask/Gamestop wallet account. You can export the Loopring related account details from the "Security" tab while logged into https://loopring.io. Make sure these details are from the same account!

DO NOT SHARE ANY API OR PRIVATE KEYS with anyone else!!!!!!!

This was written in .NET 6 so you need an IDE that can compile it. 

You will need to setup an "appsettings.json" file in the project directory like below with the property "Copy to Output Directory" set to "Copy Always".

```json
{
  "Settings": {
    "LoopringApiKey": "ksdBlahblah", //Your loopring api key.  DO NOT SHARE THIS AT ALL.
    "LoopringPrivateKey": "0xblahblah", //Your loopring private key.  DO NOT SHARE THIS AT ALL.
    "MetamaskPrivateKey": "asadasdBLahBlah", //Private key from metamask. DO NOT SHARE THIS AT ALL.
    "LoopringAddress": "0xblahabla", //Your loopring address
    "LoopringAccountId": 40940, //Your loopring account id
    "ValidUntil": 1700000000, //How long this transfer should be valid for. Shouldn't have to change this value
    "MaxFeeTokenId": 1, //The token id for the fee. 0 for ETH, 1 for LRC
    "Exchange": "0x0BABA1Ad5bE3a5C0a66E7ac838a129Bf948f1eA4" //Loopring Exchange address
  }
}
```

Lines 12-15 in the Program.cs file are what need to be changed with the nftAmount, nftTokenId, nftData and toAddress.

```csharp
string nftAmount = "1"; //the amount of the nft to transfer
int nftTokenId = 34008; //the nft tokenId, not the nftId
string nftData = "0x18c28cdd97789a7a82603b9a4618dd711660e7231cd6e14087baa858de483e32"; //the nftData, not nftId
string toAddress = "0x99fdddfdc9277404db0379009274cc98d3688f8b"; //the Address to send it to
```

A successful NFT transfer will return the following JSON response:

```json
{
  "hash": "0x1aecf4f692076ec8efe7ee4856568ce255029ee9ebbfc99138da560de353e4ac",
  "status": "processing",
  "isIdempotent": false,
  "accountId": 40940,
  "tokenId": 0,
  "storageId": 169
}
```

## Credits
Thanks to ItsMonty.eth for the original NFT Transfer code in the [LooPyMinty](https://github.com/Montspy/LooPyMinty) repo which I converted to C#.

Also thanks to Taranasus for his [LoopringSharp](https://github.com/taranasus/LoopringSharp) repo for the ECDSA signing which I also used.

I also used my own PoseidonSharp library for generating the Poseidon hashes and EDDSA signing.
