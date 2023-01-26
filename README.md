
# Video NFT Workflow

Add video NFT minting to any application with this guide outlining the workflow, enable users to create video NFTs up to 10GB.

🛠️ [Join a workshop](https://livepeer.typeform.com/web3workshops)


Do you have ideas to contribute to this guide? [Let us know](https://livepeer.typeform.com/web3guide)!

## Appendix

Overview 

Content Upload

Playback from Decentralized Storage

Create NFT Contract

Video NFT Minting




## Overview

**What is a video NFT minting workflow?**

Standard NFT workflows are commonly found inside NFT marketplaces. A user connects their wallet, uploads an asset, and mints it to a smart contract. NFT minting directly from other types of applications are gaining momentum (social apps, creator apps, etc). Often NFTs minted in an app experience are collectible inside the app itself. If NFTs were to gain more liquidity and value, they could be shared with an NFT marketplace and sold.

Newly available is the ability to mint video NFTs. It's complex and costly for NFT marketplaces to provide good video streaming experiences for large files, so they typically limit the file size to 100MB. This significantly limits the types of video content that can be minted as NFTs. Livepeer, a decentralized transcoding network, is ten times less expensive than alternatives making it possible to process video at scale.

Video NFT minting workflows can now be added to any web3 application for files up to 10GB, most NFT marketplaces limit file size uploads to 100MB.

Check out the [Long Take NFT Publisher](https://www.longtake.xyz/), a community app that demonstrates a video NFT workflow.

**Why include a video NFT workflow in your app?**

- Ensure optimal video playback on all bandwidths and device types by transcoding the video on the Livepeer network; this solves the video buffering problems that occur when playing directly from decentralized storage gateways.
- Enable the creation of video NFTs up to 10GB - most NFT marketplaces limit uploads to 100MB (this is why so many NFTs are .jpg, .gif, or videos under a minute long.)
- Owning content as an NFT is completely unique to web3. On-chain ownership provides the ability to share content as the owner chooses and smart contracts can be created to automatically distribute royalties.
- Many app experiences already lend themselves to ownable content that can be minted as an NFT - the initial social post that went viral, a memorable clip of gameplay, live music or unique behind the scenes content.

**There are four key components to adding a video NFT workflow to your app:**

- **Content Upload:** How the video is being sourced to become an NFT. The most common way to do this is by adding a drag and drop or file upload UI component. Another option is to clip video from a livestream and mint that video directly in the app experience.
- **Playback from Decentralized Storage:** The setup of the backend to ensure that the video NFT is stored and played back through Livepeer for optimized video.
- **Create NFT Contract:** The ERC721 or ERC1155 contract that is the collection of NFTs, each NFT is minted to this contract.
- **Video NFT Minting:** The end user experience of connecting their wallet, uploading the video, adding metadata, and minting.
## Content Upload

**Select File.** For existing videos (video files that have already been created), the application will need to upload them to decentralized storage. Both mobile and web platforms have native ways to select a file stored on a device - usually a button that can be clicked on to prompt the user to select the video file.

**Drag-and-drop.** For a drag-and-drop experience, there are some great open-source libraries that can be used: [Uppy](https://uppy.io/), [Dropzone.js](https://www.dropzone.dev/)

**Clip Live Video.** Another experience that can be created in an app is to clip live video and mint files within the app. This could be interesting for creating shareable clips from a long video like capturing notable gameplay moments. We couldn’t find open source code to clip a video, if you find one please [let us know](https://livepeer.typeform.com/web3guide) and we’ll add it here!
## Playback from Decentralized Storage

**Store & Play.** 

Set up IPFS with [Pinata](https://docs.pinata.cloud/), [4everland](https://docs.4everland.org/), [nft.storage](https://nft.storage/), [Lighthouse](https://www.lighthouse.storage/documentation) or [Filebase](https://docs.filebase.com/web3-education/web3-tutorials/livepeer/livepeer-mint-a-video-nft-with-livepeer). A CID will be returned after the video is uploaded, which can then be played in a frontend experience with the [Livepeer player](https://docs.livepeer.org/reference/livepeer-js/Player). The Livepeer player will automatically send the file to the Livepeer network for transcoding, playback, and caching. After the file is played one time through the Livepeer player, it is permanently transcoded for optimal playback for any viewer.

To check out other options for decentralized storage, go to the *Storage* section in [this guide](https://builderguides.livepeer.org/web3-builder-guide-short-form-video-social-apps?mc_cid=a09b18b545).

#
##  Create NFT Contract

An NFT contract is your ERC721 or ERC1155 contract that returns a URL for the storefront - this is the NFT collection. All individual NFTs are minted to a collection, the ownership of the video NFT is still held by the wallet it was minted on.

**NFT Contract.** Tools like [Moralis](https://moralis.io/), [thirdweb](https://thirdweb.com/) and [NFT Port](https://www.nftport.xyz/) make creating and interacting with contracts very easy. Some considerations when creating the contract:

- Which type of contract do you want to create: ERC 721 or ERC 1155?
- Which blockchain do you want to deploy to? Choosing to deploy on an L1 or L2 depends on the type of app, scalability of the chain, network fees, cost, and security. L2s are very fast, have low fees, and are very scalable. L1s have the highest level of security.
- Popular L1s for NFTs include [Ethereum](https://ethereum.org/en/nft/), [Solana](https://solana.com/developers/nfts), and [Tezos](https://tezos.com/non-fungible-token/); [Polygon](https://wiki.polygon.technology/docs/develop/nftstorage/) is a popular L2 chain.

Contract-Level Metadata. This includes information about the collection: name, description, image, and external link. Read more on [contract-level metadata on OpenSea](https://docs.opensea.io/docs/contract-level-metadata).
## Video NFT Minting


**Connect Wallet.** The first step in creating an NFT minting workflow is to add the connect wallet button. Two popular options for React apps are: [RainbowKit](https://www.rainbowkit.com/docs/connect-button) and [ConnectKit](https://docs.family.co/connectkit). *Note: the wallet must be set to the same chain the NFT contract is deployed on.*

**Add Metadata.** Once the file is uploaded, NFT token metadata can be added and stored in the smart contract along with the video NFT. Simple tools to use are [thirdweb](https://portal.thirdweb.com/sdk), [NFT Port](https://www.nftport.xyz/) and [Moralis](https://moralis.io/). Remember to specify the correct chain. Read more on [metadata standards from OpenSea](https://docs.opensea.io/docs/metadata-standards). Common metadata includes:

- name: name of the video NFT
- description: description of the video NFT
- animation_url: URL to the IPFS gateway (or other decentralized storage) where the mp4 video file is stored
- external_url: URL to a website where the video player is hosted; this allows for optimized playback on any NFT marketplace. For convenience, you can use the hosted version of the [Livepeer Player](https://docs.livepeer.org/reference/livepeer-js/Player).

**Hosted Player.** Livepeer has a hosted player at [https://lvpr.tv/?v=](https://lvpr.tv/?v=)<ID>. Replace <ID> with the IPFS CID, Arweave transaction hash, or other decentralized storage identifier.
## Questions on building?

[Join a workshop](https://livepeer.typeform.com/web3workshops).
Do you have ideas to contribute to this guide? [Let us know](https://livepeer.typeform.com/web3guide)!


## Video NFT Minting


**Connect Wallet.** The first step in creating an NFT minting workflow is to add the connect wallet button. Two popular options for React apps are: [RainbowKit](https://www.rainbowkit.com/docs/connect-button) and [ConnectKit](https://docs.family.co/connectkit). *Note: the wallet must be set to the same chain the NFT contract is deployed on.*

**Add Metadata.** Once the file is uploaded, NFT token metadata can be added and stored in the smart contract along with the video NFT. Simple tools to use are [thirdweb](https://portal.thirdweb.com/sdk), [NFT Port](https://www.nftport.xyz/) and [Moralis](https://moralis.io/). Remember to specify the correct chain. Read more on [metadata standards from OpenSea](https://docs.opensea.io/docs/metadata-standards). Common metadata includes:

- name: name of the video NFT
- description: description of the video NFT
- animation_url: URL to the IPFS gateway (or other decentralized storage) where the mp4 video file is stored
- external_url: URL to a website where the video player is hosted; this allows for optimized playback on any NFT marketplace. For convenience, you can use the hosted version of the [Livepeer Player](https://docs.livepeer.org/reference/livepeer-js/Player).

**Hosted Player.** Livepeer has a hosted player at [https://lvpr.tv/?v=](https://lvpr.tv/?v=)<ID>. Replace <ID> with the IPFS CID, Arweave transaction hash, or other decentralized storage identifier.
## Contributors

[@SuhailKakar](https://github.com/SuhailKakar) &
[@danielapassos](https://github.com/danielapassos)
