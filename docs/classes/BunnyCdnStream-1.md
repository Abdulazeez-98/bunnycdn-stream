[bunnycdn-stream](../README.md) / [Exports](../modules.md) / BunnyCdnStream

# Class: BunnyCdnStream

## Table of contents

### Constructors

- [constructor](BunnyCdnStream-1.md#constructor)

### Properties

- [axiosOptions](BunnyCdnStream-1.md#axiosoptions)
- [options](BunnyCdnStream-1.md#options)

### Methods

- [addCaptions](BunnyCdnStream-1.md#addcaptions)
- [createAndUploadVideo](BunnyCdnStream-1.md#createanduploadvideo)
- [createCollection](BunnyCdnStream-1.md#createcollection)
- [createDirectUpload](BunnyCdnStream-1.md#createdirectupload)
- [createVideo](BunnyCdnStream-1.md#createvideo)
- [deleteAllCollections](BunnyCdnStream-1.md#deleteallcollections)
- [deleteAllVideos](BunnyCdnStream-1.md#deleteallvideos)
- [deleteCaptions](BunnyCdnStream-1.md#deletecaptions)
- [deleteCollection](BunnyCdnStream-1.md#deletecollection)
- [deleteVideo](BunnyCdnStream-1.md#deletevideo)
- [fetchVideo](BunnyCdnStream-1.md#fetchvideo)
- [generateTUSHash](BunnyCdnStream-1.md#generatetushash)
- [getCollection](BunnyCdnStream-1.md#getcollection)
- [getOptions](BunnyCdnStream-1.md#getoptions)
- [getVideo](BunnyCdnStream-1.md#getvideo)
- [getVideoHeatmap](BunnyCdnStream-1.md#getvideoheatmap)
- [getVideoStatistics](BunnyCdnStream-1.md#getvideostatistics)
- [listAllCollections](BunnyCdnStream-1.md#listallcollections)
- [listAllVideos](BunnyCdnStream-1.md#listallvideos)
- [listCollections](BunnyCdnStream-1.md#listcollections)
- [listVideos](BunnyCdnStream-1.md#listvideos)
- [reencodeVideo](BunnyCdnStream-1.md#reencodevideo)
- [request](BunnyCdnStream-1.md#request)
- [setThumbnail](BunnyCdnStream-1.md#setthumbnail)
- [updateCollection](BunnyCdnStream-1.md#updatecollection)
- [updateVideo](BunnyCdnStream-1.md#updatevideo)
- [uploadVideo](BunnyCdnStream-1.md#uploadvideo)

## Constructors

### constructor

• **new BunnyCdnStream**(`options`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `options` | [`Options`](../interfaces/BunnyCdnStream.Options.md) |

#### Defined in

[src/index.ts:30](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L30)

## Properties

### axiosOptions

• **axiosOptions**: [`BunnyAxiosRequestConfig`](../interfaces/BunnyCdnStream.BunnyAxiosRequestConfig.md)

#### Defined in

[src/index.ts:18](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L18)

___

### options

• **options**: [`Options`](../interfaces/BunnyCdnStream.Options.md)

Options for connecting and authenticating with the Bunny CDN API

#### Defined in

[src/index.ts:28](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L28)

## Methods

### addCaptions

▸ **addCaptions**(`videoId`, `data`): `Promise`<[`AddCaptionsVideoResponse`](../interfaces/BunnyCdnStream.AddCaptionsVideoResponse.md)\>

Add captions to a video

**`Example`**

```typescript
await stream.addCaptions("0273f24a-79d1-d0fe-97ca-b0e36bed31es", { captionsFile: readFile("./subtitles.srt"), label: "English", srclang: "en" })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |
| `data` | `Object` | The data to add captions with where the captions file is a buffer or base64 string |
| `data.captionsFile` | `string` \| `Buffer` | - |
| `data.label` | `string` | - |
| `data.srclang` | `string` | - |

#### Returns

`Promise`<[`AddCaptionsVideoResponse`](../interfaces/BunnyCdnStream.AddCaptionsVideoResponse.md)\>

A [AddCaptionsVideoResponse](../interfaces/BunnyCdnStream.AddCaptionsVideoResponse.md) instance.

#### Defined in

[src/index.ts:358](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L358)

___

### createAndUploadVideo

▸ **createAndUploadVideo**(`file`, `data`): `Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

Create and upload a video in one function

**`Example`**

```typescript
await stream.createAndUploadVideo(createReadStream("./file.mp4"), { title: "The best title" })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `file` | `ReadStream` | The video file to upload as a readable stream |
| `data` | `Object` | The data to create the video with |
| `data.collectionId?` | `string` | - |
| `data.title` | `string` | - |

#### Returns

`Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

A [VideoResponse](../interfaces/BunnyCdnStream.VideoResponse.md) instance.

#### Defined in

[src/index.ts:168](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L168)

___

### createCollection

▸ **createCollection**(`name`): `Promise`<[`CreateCollectionResponse`](../interfaces/BunnyCdnStream.CreateCollectionResponse.md)\>

Create a collection

**`Example`**

```typescript
await stream.createCollection("New Collection")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `name` | `string` | The collection name |

#### Returns

`Promise`<[`CreateCollectionResponse`](../interfaces/BunnyCdnStream.CreateCollectionResponse.md)\>

A [CreateCollectionResponse](../interfaces/BunnyCdnStream.CreateCollectionResponse.md) instance.

#### Defined in

[src/index.ts:397](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L397)

___

### createDirectUpload

▸ **createDirectUpload**(`data`, `expirationDate?`): `Promise`<[`CreateDirectUpload`](../interfaces/BunnyCdnStream.CreateDirectUpload.md)\>

Generate a direct upload tus

NOTE: metadata.filetype is required for the tus upload to work

**`Example`**

```typescript
await stream.createDirectUpload({ title: "My Video" })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Object` | The data to create the video with |
| `data.collection?` | `string` | - |
| `data.title` | `string` | - |
| `expirationDate?` | `Date` | - |

#### Returns

`Promise`<[`CreateDirectUpload`](../interfaces/BunnyCdnStream.CreateDirectUpload.md)\>

A [CreateDirectUpload](../interfaces/BunnyCdnStream.CreateDirectUpload.md)

#### Defined in

[src/index.ts:539](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L539)

___

### createVideo

▸ **createVideo**(`data`): `Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

Create a video, this does not upload the video file

**`Example`**

```typescript
await stream.createVideo({ title: "The best title" })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Object` | The data to create the video with |
| `data.collectionId?` | `string` | - |
| `data.title` | `string` | - |

#### Returns

`Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

A [VideoResponse](../interfaces/BunnyCdnStream.VideoResponse.md) instance.

#### Defined in

[src/index.ts:126](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L126)

___

### deleteAllCollections

▸ **deleteAllCollections**(): `Promise`<`void`\>

Delete all collections

**`Example`**

```typescript
await stream.deleteAllCollections()
```

#### Returns

`Promise`<`void`\>

void

#### Defined in

[src/index.ts:516](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L516)

___

### deleteAllVideos

▸ **deleteAllVideos**(): `Promise`<`void`\>

Delete all videos

NOTE: This uses the listVideos method and will iterate over all pages and delete all videos per page before continuing to the next page.

**`Example`**

```typescript
await stream.deleteAllVideos();
```

#### Returns

`Promise`<`void`\>

void

#### Defined in

[src/index.ts:106](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L106)

___

### deleteCaptions

▸ **deleteCaptions**(`videoId`, `srclang`): `Promise`<[`DeleteCaptionsVideoResponse`](../interfaces/BunnyCdnStream.DeleteCaptionsVideoResponse.md)\>

Delete captions from a video

**`Example`**

```typescript
await stream.deleteCaptions("0273f24a-79d1-d0fe-97ca-b0e36bed31es", "en")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |
| `srclang` | `string` | The specified srclang used when creating |

#### Returns

`Promise`<[`DeleteCaptionsVideoResponse`](../interfaces/BunnyCdnStream.DeleteCaptionsVideoResponse.md)\>

A [DeleteCaptionsVideoResponse](../interfaces/BunnyCdnStream.DeleteCaptionsVideoResponse.md) instance.

#### Defined in

[src/index.ts:381](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L381)

___

### deleteCollection

▸ **deleteCollection**(`collectionId`): `Promise`<[`DeleteCollectionResponse`](../interfaces/BunnyCdnStream.DeleteCollectionResponse.md)\>

Delete a collection

**`Example`**

```typescript
await stream.deleteCollection("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `collectionId` | `string` | The collection ID |

#### Returns

`Promise`<[`DeleteCollectionResponse`](../interfaces/BunnyCdnStream.DeleteCollectionResponse.md)\>

A [DeleteCollectionResponse](../interfaces/BunnyCdnStream.DeleteCollectionResponse.md) instance.

#### Defined in

[src/index.ts:501](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L501)

___

### deleteVideo

▸ **deleteVideo**(`videoId`): `Promise`<[`DeleteVideoResponse`](../interfaces/BunnyCdnStream.DeleteVideoResponse.md)\>

Delete a video

**`Example`**

```typescript
await stream.deleteVideo("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |

#### Returns

`Promise`<[`DeleteVideoResponse`](../interfaces/BunnyCdnStream.DeleteVideoResponse.md)\>

A [DeleteVideoResponse](../interfaces/BunnyCdnStream.DeleteVideoResponse.md) instance.

#### Defined in

[src/index.ts:88](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L88)

___

### fetchVideo

▸ **fetchVideo**(`videoId`, `data`): `Promise`<[`FetchVideoResponse`](../interfaces/BunnyCdnStream.FetchVideoResponse.md)\>

Upload a video using a URL

NOTE: This will not work if the video is not public, and the thumbnail/preview will not be regenerated for existing videos

**`Example`**

```typescript
await stream.fetchVideo("0273f24a-79d1-d0fe-97ca-b0e36bed31es", { url: "https://example.com/file.mp4" })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |
| `data` | `Object` | The data with video url to fetch and optional headers |
| `data.headers?` | `Object` | - |
| `data.url` | `string` | - |

#### Returns

`Promise`<[`FetchVideoResponse`](../interfaces/BunnyCdnStream.FetchVideoResponse.md)\>

A [FetchVideoResponse](../interfaces/BunnyCdnStream.FetchVideoResponse.md) instance

#### Defined in

[src/index.ts:339](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L339)

___

### generateTUSHash

▸ `Private` **generateTUSHash**(`videoId`, `expirationTime`): `string`

#### Parameters

| Name | Type |
| :------ | :------ |
| `videoId` | `string` |
| `expirationTime` | `number` |

#### Returns

`string`

#### Defined in

[src/index.ts:562](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L562)

___

### getCollection

▸ **getCollection**(`collectionId`): `Promise`<[`BunnyCdnStreamCollection`](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md)\>

Retrieve info about a collection from BunnyCdn

**`Example`**

```typescript
await stream.getCollection("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `collectionId` | `string` | The collection ID |

#### Returns

`Promise`<[`BunnyCdnStreamCollection`](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md)\>

A [BunnyCdnStreamCollection](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md) instance.

#### Defined in

[src/index.ts:414](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L414)

___

### getOptions

▸ `Private` **getOptions**(): `Object`

#### Returns

`Object`

| Name | Type |
| :------ | :------ |
| `adapter?` | `AxiosAdapterConfig` \| `AxiosAdapterConfig`[] |
| `auth?` | `AxiosBasicCredentials` |
| `baseURL?` | `string` |
| `beforeRedirect?` | (`options`: `Record`<`string`, `any`\>, `responseDetails`: { `headers`: `Record`<`string`, `string`\>  }) => `void` |
| `cancelToken?` | `CancelToken` |
| `data?` | `any` |
| `decompress?` | `boolean` |
| `env?` | { `FormData?`: (...`args`: `any`[]) => `object`  } |
| `env.FormData?` | (...`args`: `any`[]) => `object` |
| `formSerializer?` | `FormSerializerOptions` |
| `headers` | `AxiosHeaders` |
| `httpAgent?` | `any` |
| `httpsAgent?` | `any` |
| `insecureHTTPParser?` | `boolean` |
| `maxBodyLength?` | `number` |
| `maxContentLength?` | `number` |
| `maxRate?` | `number` \| [`number`, `number`] |
| `maxRedirects?` | `number` |
| `method?` | `string` |
| `onDownloadProgress?` | (`progressEvent`: `AxiosProgressEvent`) => `void` |
| `onUploadProgress?` | (`progressEvent`: `AxiosProgressEvent`) => `void` |
| `params?` | `any` |
| `paramsSerializer?` | `ParamsSerializerOptions` |
| `proxy?` | ``false`` \| `AxiosProxyConfig` |
| `responseEncoding?` | `string` |
| `responseType?` | `ResponseType` |
| `signal?` | `GenericAbortSignal` |
| `socketPath?` | ``null`` \| `string` |
| `timeout?` | `number` |
| `timeoutErrorMessage?` | `string` |
| `transformRequest?` | `AxiosRequestTransformer` \| `AxiosRequestTransformer`[] |
| `transformResponse?` | `AxiosResponseTransformer` \| `AxiosResponseTransformer`[] |
| `transitional?` | `TransitionalOptions` |
| `url?` | `string` |
| `validateStatus?` | ``null`` \| (`status`: `number`) => `boolean` |
| `withCredentials?` | `boolean` |
| `xsrfCookieName?` | `string` |
| `xsrfHeaderName?` | `string` |

#### Defined in

[src/index.ts:593](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L593)

___

### getVideo

▸ **getVideo**(`videoId`): `Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

Retrieve a video from BunnyCdn

**`Example`**

```typescript
await stream.getVideo("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |

#### Returns

`Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

A [VideoResponse](../interfaces/BunnyCdnStream.VideoResponse.md) instance.

#### Defined in

[src/index.ts:44](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L44)

___

### getVideoHeatmap

▸ **getVideoHeatmap**(`videoId`): `Promise`<[`VideoHeatmapResponse`](../interfaces/BunnyCdnStream.VideoHeatmapResponse.md)\>

Get video statistics

**`Example`**

```typescript
await stream.getVideoHeatmap("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video id to get heatmap info from |

#### Returns

`Promise`<[`VideoHeatmapResponse`](../interfaces/BunnyCdnStream.VideoHeatmapResponse.md)\>

A [VideoHeatmapResponse](../interfaces/BunnyCdnStream.VideoHeatmapResponse.md) instance.

#### Defined in

[src/index.ts:185](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L185)

___

### getVideoStatistics

▸ **getVideoStatistics**(`videoId`, `data?`): `Promise`<[`VideoStatisticsResponse`](../interfaces/BunnyCdnStream.VideoStatisticsResponse.md)\>

Get video statistics

**`Example`**

```typescript
await stream.getVideoStatistics("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | - |
| `data` | `Object` | The data to fetch video statistics with |
| `data.dateFrom?` | `string` | - |
| `data.dateTo?` | `string` | - |
| `data.hourly?` | `boolean` | - |

#### Returns

`Promise`<[`VideoStatisticsResponse`](../interfaces/BunnyCdnStream.VideoStatisticsResponse.md)\>

A [VideoStatisticsResponse](../interfaces/BunnyCdnStream.VideoStatisticsResponse.md) instance.

#### Defined in

[src/index.ts:202](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L202)

___

### listAllCollections

▸ **listAllCollections**(`data?`, `stop?`): `Promise`<[`BunnyCdnStreamCollection`](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md)[]\>

List all collections with an optional callback between each page

**`Example`**

```typescript
await stream.listAllCollections()
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Object` | The options to list collections with |
| `data.itemsPerPage?` | `number` | - |
| `data.orderBy?` | `string` | - |
| `data.search?` | `string` | - |
| `stop?` | (`collections`: [`BunnyCdnStreamCollection`](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md)[], `page`: `number`, `totalPages`: `number`) => `boolean` | The callback that if returns ``true`` stops the iteration |

#### Returns

`Promise`<[`BunnyCdnStreamCollection`](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md)[]\>

An array of [BunnyCdnStreamCollection](../interfaces/BunnyCdnStream.BunnyCdnStreamCollection.md) instances.

#### Defined in

[src/index.ts:447](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L447)

___

### listAllVideos

▸ **listAllVideos**(`data?`, `stop?`): `Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)[]\>

List all videos with an optional callback between each page

**`Example`**

```typescript
await stream.listAllVideos()
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Object` | The options to list videos with |
| `data.collection?` | `string` | - |
| `data.itemsPerPage?` | `number` | - |
| `data.orderBy?` | `string` | - |
| `data.search?` | `string` | - |
| `stop?` | (`videos`: [`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)[], `page`: `number`, `totalPages`: `number`) => `boolean` | The callback that if returns ``true`` stops the iteration |

#### Returns

`Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)[]\>

An array of [VideoStatisticsResponse](../interfaces/BunnyCdnStream.VideoStatisticsResponse.md) instances.

#### Defined in

[src/index.ts:266](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L266)

___

### listCollections

▸ **listCollections**(`data?`): `Promise`<[`ListCollectionsResponse`](../interfaces/BunnyCdnStream.ListCollectionsResponse.md)\>

List collections

**`Example`**

```typescript
await stream.listCollections({ page: 2, search: "Y collections", itemsPerPage: 100, orderBy: 'date' })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Object` | The options to list collections with |
| `data.itemsPerPage?` | `number` | - |
| `data.orderBy?` | `string` | - |
| `data.page?` | `number` | - |
| `data.search?` | `string` | - |

#### Returns

`Promise`<[`ListCollectionsResponse`](../interfaces/BunnyCdnStream.ListCollectionsResponse.md)\>

a [ListCollectionsResponse](../interfaces/BunnyCdnStream.ListCollectionsResponse.md) instances.

#### Defined in

[src/index.ts:429](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L429)

___

### listVideos

▸ **listVideos**(`data?`): `Promise`<{ `currentPage`: `number` ; `items`: [`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)[] ; `itemsPerPage`: `number` ; `totalItems`: `number`  }\>

List videos

**`Example`**

```typescript
await stream.listVideos({ page: 2, search: "The best title", itemsPerPage: 10 })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Object` | The options to list videos with |
| `data.collection?` | `string` | - |
| `data.itemsPerPage?` | `number` | - |
| `data.orderBy?` | `string` | - |
| `data.page?` | `number` | - |
| `data.search?` | `string` | - |

#### Returns

`Promise`<{ `currentPage`: `number` ; `items`: [`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)[] ; `itemsPerPage`: `number` ; `totalItems`: `number`  }\>

An array of [VideoStatisticsResponse](../interfaces/BunnyCdnStream.VideoStatisticsResponse.md) instances.

#### Defined in

[src/index.ts:247](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L247)

___

### reencodeVideo

▸ **reencodeVideo**(`videoId`): `Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

Force re-encode a video

NOTE: This will not work if keepOriginal is set to false

**`Example`**

```typescript
await stream.reencodeVideo("0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |

#### Returns

`Promise`<[`BunnyCdnStreamVideo`](BunnyCdnStreamVideo.md)\>

A [VideoResponse](../interfaces/BunnyCdnStream.VideoResponse.md) instance.

#### Defined in

[src/index.ts:228](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L228)

___

### request

▸ `Private` **request**<`ResponseType`\>(`options`, `name`): `Promise`<`ResponseType`\>

#### Type parameters

| Name | Type |
| :------ | :------ |
| `ResponseType` | extends `Record`<`string`, `any`\> |

#### Parameters

| Name | Type |
| :------ | :------ |
| `options` | `AxiosRequestConfig`<`any`\> |
| `name` | `string` |

#### Returns

`Promise`<`ResponseType`\>

#### Defined in

[src/index.ts:569](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L569)

___

### setThumbnail

▸ **setThumbnail**(`videoId`, `thumbnail`, `overrideContentType?`): `Promise`<[`SetThumbnailVideoResponse`](../interfaces/BunnyCdnStream.SetThumbnailVideoResponse.md)\>

Set the thumbnail

NOTE: The file type is automatically detected from the buffer, however if it fails, it will default to ``image/jpeg``

**`Example`**

```typescript
await stream.setThumbnail("0273f24a-79d1-d0fe-97ca-b0e36bed31es", readFileSync("thumbnail.jpg"))
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |
| `thumbnail` | `string` \| `ReadStream` \| `Buffer` | A buffer/stream/url of the thumbnail |
| `overrideContentType?` | `string` | The content type to override and skip the automatic detection |

#### Returns

`Promise`<[`SetThumbnailVideoResponse`](../interfaces/BunnyCdnStream.SetThumbnailVideoResponse.md)\>

A [SetThumbnailVideoResponse](../interfaces/BunnyCdnStream.SetThumbnailVideoResponse.md) instance.

#### Defined in

[src/index.ts:307](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L307)

___

### updateCollection

▸ **updateCollection**(`collectionId`, `data`): `Promise`<[`UpdateCollectionResponse`](../interfaces/BunnyCdnStream.UpdateCollectionResponse.md)\>

Update info of a collection

**`Example`**

```typescript
await stream.updateCollection("0273f24a-79d1-d0fe-97ca-b0e36bed31es", { name: 'New Collection'})
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `collectionId` | `string` | The collection ID |
| `data` | `Object` | - |
| `data.name` | `string` | - |

#### Returns

`Promise`<[`UpdateCollectionResponse`](../interfaces/BunnyCdnStream.UpdateCollectionResponse.md)\>

A [UpdateCollectionResponse](../interfaces/BunnyCdnStream.UpdateCollectionResponse.md) instance.

#### Defined in

[src/index.ts:484](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L484)

___

### updateVideo

▸ **updateVideo**(`videoId`, `data?`): `Promise`<[`UpdateVideoResponse`](../interfaces/BunnyCdnStream.UpdateVideoResponse.md)\>

Update video information

**`Example`**

```typescript
await stream.updateVideo("0273f24a-79d1-d0fe-97ca-b0e36bed31es", { title: "New title" })
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `videoId` | `string` | The video ID |
| `data` | `Object` | The data to update |
| `data.chapters?` | { `end`: `number` ; `start`: `number` ; `title`: `string`  }[] | - |
| `data.collectionId?` | `string` | - |
| `data.metaTags?` | { `property`: `string` ; `value`: `string`  }[] | - |
| `data.moments?` | { `label`: `string` ; `timestamp`: `number`  }[] | - |
| `data.title?` | `string` | - |

#### Returns

`Promise`<[`UpdateVideoResponse`](../interfaces/BunnyCdnStream.UpdateVideoResponse.md)\>

A [VideoResponse](../interfaces/BunnyCdnStream.VideoResponse.md) instance.

#### Defined in

[src/index.ts:61](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L61)

___

### uploadVideo

▸ **uploadVideo**(`file`, `videoId`, `data?`): `Promise`<[`UploadVideoResponse`](../interfaces/BunnyCdnStream.UploadVideoResponse.md)\>

Upload video, this does not create the video and requires a created video

**`Example`**

```typescript
await stream.uploadVideo(createReadStream("./file.mp4"), "0273f24a-79d1-d0fe-97ca-b0e36bed31es")
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `file` | `ReadStream` | The video file to upload as a readable stream |
| `videoId` | `string` | The video id to upload to of a created video |
| `data?` | `Object` | Optional paramaters such as enabledResolutions |
| `data.enabledResolutions?` | `string` | - |

#### Returns

`Promise`<[`UploadVideoResponse`](../interfaces/BunnyCdnStream.UploadVideoResponse.md)\>

A [UploadVideoResponse](../interfaces/BunnyCdnStream.UploadVideoResponse.md) instance.

#### Defined in

[src/index.ts:147](https://github.com/dan-online/bunnycdn-stream/blob/26b06e1/src/index.ts#L147)
