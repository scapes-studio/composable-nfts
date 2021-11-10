# Composable NFTs

While the extensions [defined by OpenSea](https://docs.opensea.io/docs/metadata-standards) can form a base layer framework to the [ERC-721 metadata standard](https://eips.ethereum.org/EIPS/eip-721#specification), they fail to define configuration standards that enable NFTs in different composable contexts.

The following extensions to the ERC 721 metadata standard ensure your project can integrate with other third-party composable projects like the [PunkScape Builder](https://punkscape.xyz/builder).

## Transparent Compatibility

The `transparent_image` field is required unless your image is already transparent and has a `background_color` defined. The `background_color` field is optional, but recommended.

```json
{
  "image": "ipfs://...",
  "transparent_image": "ipfs://...",
  "background_color": "#000000"
}
```

## Pixel Art Compatibility

The `pixel_density` field refers to the conceptual not literal pixel density, the perceived pixel width and height of the image. For example, even if the image of a CryptoPunk could be 600px * 600px, the pixel density, for the purposes of composability, is 24px * 24px.
`pixel_density.width` and `pixel_density.height` are required fields for pixel art compatability as described below:

```json
{
  "image": "ipfs://...",
  "pixel_density": {
    "width": 24,
    "height": 24
  }
}
```

If the pixel density is equal across all tokens, it can be defined at the contract level metadata, rather than the individual NFT level metadata, via `token_pixel_density` (as described [here](https://docs.opensea.io/docs/contract-level-metadata)), as follows:

```json
{
  "name": "NFT Project XYZ",
  "description": "A wonderful NFT collection configured for composability",
  "image": "https://nft-project.xyz/logo.png",
  "external_link": "https://nft-project.xyz",
  "seller_fee_basis_points": 100,
  "fee_recipient": "0x123",
  "token_pixel_density": {
    "width": 24,
    "height": 24,
  }
}
```
If you have suggestions to extend this standard, please feel free to create a pull request or submit a GitHub issue.
