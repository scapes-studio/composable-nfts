# Composable NFTs

The [ERC-721 metadata](https://eips.ethereum.org/EIPS/eip-721#specification) standard and the extensions [defined by OpenSea](https://docs.opensea.io/docs/metadata-standards) are a great base layer framework do define token metadata but fall short in defining configuration standards that enable us to use our NFTs in different contexts.

The following configuration options power the [PunkScape Builder](https://punkscape.xyz/builder). If you have suggestions to extend this standard, please feel free to create a pull request or submit a GitHub issue.

## Transparent Compatibility

By following this extension to the ERC721 metadata standard you make sure your project is compatible with (`transparent_image`, `pixel_density.width`, `pixel_density.height`):

```json
{
  "image": "ipfs://...",
  "transparent_image": "ipfs://...",
  "background_color": "#000000"
}
```

...with `transparent_image` being *required* and `background_color` being *suggested but not required*. If your `image` already is transparent and `background_color` is defined, the `transparent_image` configuration can be omitted.


## Pixel Art Compatibility

To enable composability of pixel art NFTs, the `pixel_density` field defines the actual width and height in pixels of the image. Even if the image of a CryptoPunk could be 600px * 600px, the actual pixel density is 24px * 24px.

```json
{
  "image": "ipfs://...",
  "pixel_density": {
    "width": 24,
    "height": 24
  }
}
```

...with `pixel_density` being a *strong suggestion*.

If the pixel density is equal across all tokens, it can be defined in the contract level metadata via `token_pixel_density` (as described [here](https://docs.opensea.io/docs/contract-level-metadata)) instead:

```json
{
  "name": "NFT Project XYZ",
  "description": "The wonderful NFT collection blah",
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
