# Reference
## Deployment
<details><summary><code>client.deployment.licenseStatus() -> DeploymentLicenseStatusResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.deployment().licenseStatus();
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc
<details><summary><code>client.doc.head(docId) -> DocHead200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().head(
    "docId",
    HeadDocRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.download(docId, layerName) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().download(
    "docId",
    "layerName",
    DownloadDocRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.manifest(docId, layerName) -> DocManifest200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().manifest(
    "docId",
    "layerName",
    ManifestDocRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.render(docId, layerName, pon) -> InputStream</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Render parameters (viewport, format) pass as flat dotted query keys, e.g. `?viewport.kind=width&viewport.width=800`; the full grammar is documented with the viewer.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().render(
    "docId",
    "layerName",
    1,
    RenderDocRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `Integer` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.text(docId, layerName, pon) -> DocText200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().text(
    "docId",
    "layerName",
    1,
    TextDocRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `Integer` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Shares
<details><summary><code>client.shares.exchange(request) -> SharesExchange200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Unauthenticated, but requires a browser Origin header, checked against the grant allowlist. Unknown, revoked, and disabled tokens are indistinguishable (404). Passphrase-protected grants return 422 SharePasswordRequired until `password` is supplied. Mounted only when the deployment can sign (HS256 mode).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.shares().exchange(
    SharesExchangeRequest
        .builder()
        .shareToken("shareToken")
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**shareToken:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**password:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.shares.list(tenantId) -> SharesList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.shares().list(
    "tenantId",
    ListSharesRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**limit:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**docId:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.shares.create(tenantId, request) -> SharesCreate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The returned share id IS the public share token. Mounted only when the deployment can sign (HS256 mode) — exchange mints session JWTs, so grants exist only where minting does.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.shares().create(
    "tenantId",
    SharesCreateRequest
        .builder()
        .docId("docId")
        .scope(
            Arrays.asList("scope")
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**scope:** `List<String>` 
    
</dd>
</dl>

<dl>
<dd>

**origins:** `Optional<List<String>>` 
    
</dd>
</dl>

<dl>
<dd>

**password:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**sessionTtlSeconds:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**expiresAt:** `Optional<Integer>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.shares.get(tenantId, shareId) -> SharesGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.shares().get(
    "tenantId",
    "shareId",
    GetSharesRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**shareId:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.shares.delete(tenantId, shareId)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.shares().delete(
    "tenantId",
    "shareId",
    DeleteSharesRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**shareId:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.shares.update(tenantId, shareId, request) -> SharesUpdate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.shares().update(
    "tenantId",
    "shareId",
    SharesUpdateRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**shareId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**scope:** `Optional<List<String>>` 
    
</dd>
</dl>

<dl>
<dd>

**origins:** `Optional<List<String>>` 
    
</dd>
</dl>

<dl>
<dd>

**password:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**sessionTtlSeconds:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**disabled:** `Optional<Boolean>` 
    
</dd>
</dl>

<dl>
<dd>

**expiresAt:** `Optional<Integer>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Tenants
<details><summary><code>client.tenants.list() -> TenantsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().list(
    ListTenantsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**limit:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.create(request) -> TenantsCreate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().create(
    TenantsCreateRequest
        .builder()
        .id("id")
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**name:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.get(tenantId) -> TenantsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().get(
    "tenantId",
    GetTenantsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.delete(tenantId)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Destroys the tenant and everything in its namespace — documents, layers, stored bytes, audit history. Irreversible.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().delete(
    "tenantId",
    DeleteTenantsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.resume(tenantId)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().resume(
    "tenantId",
    ResumeTenantsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.suspend(tenantId, request)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Instantly reversible with resume. The API token is exempt, so a suspended tenant can still be inspected, exported, resumed, or deleted.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().suspend(
    "tenantId",
    TenantsSuspendRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**reason:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.usage(tenantId) -> TenantsUsage200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Facts only — no limits or billing state. Views count share exchanges plus authorized /v1/access grants, deduplicated across the two.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tenants().usage(
    "tenantId",
    UsageTenantsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**period:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Documents
<details><summary><code>client.documents.list(tenantId) -> DocumentsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().list(
    "tenantId",
    ListDocumentsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**limit:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**state:** `Optional<ListDocumentsRequestState>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.get(tenantId, id) -> DocumentsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().get(
    "tenantId",
    "id",
    GetDocumentsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.delete(tenantId, id)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().delete(
    "tenantId",
    "id",
    DeleteDocumentsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.commit(tenantId, id, request) -> DocumentsCommit200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().commit(
    "tenantId",
    "id",
    DocumentsCommitRequest
        .builder()
        .sha256("sha256")
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**sha256:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.download(tenantId, id) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().download(
    "tenantId",
    "id",
    DownloadDocumentsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.thumbnail(tenantId, id) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().thumbnail(
    "tenantId",
    "id",
    ThumbnailDocumentsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.uploadProxy(tenantId, id, request) -> DocumentsUploadProxy200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

This bounded origin-mediated fallback must only be used after documents.init returns upload.kind=proxy. Auto mode prefers a presigned object-store PUT whenever available.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().uploadProxy(
    "tenantId",
    "id",
    null,
    UploadProxyDocumentsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.importFrom(tenantId, request) -> DocumentsImportFrom200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Default mode is synchronous and bounded: the response returns only after the transfer verified and committed (or failed). mode=async (connection sources only) answers 202 immediately and an in-process worker performs the transfer with leased, fenced retries; poll the document until ready/failed. The deployment import policy gates scheme, network range, and size; sources must declare a length. CloudPDF copies and owns the bytes — the source is never referenced in place. A 502 marks a retryable upstream failure: retry with the same idempotencyKey to resume the same document. URL sources are capabilities and never echoed back. Connection sources name operator-registered storage (bucket/prefix scope, allowed credential classes, and tenant bindings are deployment configuration); `revision` is provider-interpreted (S3 VersionId, GCS generation, Azure version id).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().importFrom(
    "tenantId",
    DocumentsImportFromRequest
        .builder()
        .source(
            DocumentsImportFromRequestSource.url(
                DocumentsImportFromRequestSourceUrl
                    .builder()
                    .url("url")
                    .build()
            )
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**source:** `DocumentsImportFromRequestSource` — Where CloudPDF pulls the bytes from. The two shapes differ in WHO supplies the authority to read, not in which storage vendor holds the file.
    
</dd>
</dl>

<dl>
<dd>

**expected:** `Optional<DocumentsImportFromRequestExpected>` — Integrity pins, enforced when present. When absent, the server-observed values become authoritative.
    
</dd>
</dl>

<dl>
<dd>

**metadata:** `Optional<Map<String, Object>>` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Retrying with the same key resumes the same document rather than importing a second copy — including after a 502.
    
</dd>
</dl>

<dl>
<dd>

**dedupMode:** `Optional<DocumentsImportFromRequestDedupMode>` — always-create (default) creates a new document every time. reuse-existing returns a document that already holds the same content instead of storing it twice.
    
</dd>
</dl>

<dl>
<dd>

**docId:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**mode:** `Optional<DocumentsImportFromRequestMode>` — sync (default) holds the response open for the whole transfer. async answers 202 with the document pending and transfers in the background; it requires a connection source, and filesystem connections additionally require expected.sha256.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.init(tenantId, request) -> DocumentsInit200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().init(
    "tenantId",
    DocumentsInitRequest
        .builder()
        .contentLength(1.1)
        .contentSha256("contentSha256")
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**contentLength:** `Double` 
    
</dd>
</dl>

<dl>
<dd>

**contentSha256:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**metadata:** `Optional<Map<String, Object>>` 
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**dedupMode:** `Optional<DocumentsInitRequestDedupMode>` — always-create (default) creates a new document every time. reuse-existing returns a document that already holds the same content instead of storing it twice.
    
</dd>
</dl>

<dl>
<dd>

**docId:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**uploadTtlSec:** `Optional<Double>` 
    
</dd>
</dl>

<dl>
<dd>

**uploadPreference:** `Optional<DocumentsInitRequestUploadPreference>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Tokens
<details><summary><code>client.tokens.issue(tenantId, request) -> TokensIssue200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

kind "tenant" requires the API token — authority mints only downward. Mounted only when the deployment can sign (HS256 mode); asymmetric deployments mint with their own private key.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tokens().issue(
    "tenantId",
    IssueTokensRequest
        .builder()
        .body(
            TokensIssueRequest.doc(
                TokensIssueRequestDoc
                    .builder()
                    .sub("sub")
                    .docId("docId")
                    .expiresIn(1)
                    .scope(
                        Arrays.asList("scope")
                    )
                    .build()
            )
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `TokensIssueRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tokens.revoke(tenantId, jti, request)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Mounted only when the deployment enables token revocation.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.tokens().revoke(
    "tenantId",
    "jti",
    TokensRevokeRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenantId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**jti:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**reason:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**expiresAtSeconds:** `Optional<Integer>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Annotations
<details><summary><code>client.doc.annotations.list(docId, layerName, pon) -> DocAnnotationsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().list(
    "docId",
    "layerName",
    1,
    ListAnnotationsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `Integer` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.create(docId, layerName, pon, request) -> DocAnnotationsCreate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Doc JWTs may instead carry collab scopes (annotations:create:self, …) that refine per-annotation authorship rules; the API token is exempt from both.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().create(
    "docId",
    "layerName",
    1,
    CreateAnnotationsRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `Integer` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.delete(docId, layerName, pon, annotKey) -> DocAnnotationsDelete200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().delete(
    "docId",
    "layerName",
    1,
    "annotKey",
    DeleteAnnotationsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `Integer` 
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.update(docId, layerName, pon, annotKey, request) -> DocAnnotationsUpdate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().update(
    "docId",
    "layerName",
    1,
    "annotKey",
    UpdateAnnotationsRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `Integer` 
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Forms
<details><summary><code>client.doc.forms.get(docId, layerName) -> DocFormsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().get(
    "docId",
    "layerName",
    GetFormsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.exportData(docId, layerName) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().exportData(
    "docId",
    "layerName",
    ExportDataFormsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**format:** `Optional<ExportDataFormsRequestFormat>` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.importData(docId, layerName, request) -> DocFormsImportData200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().importData(
    "docId",
    "layerName",
    ImportDataFormsRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.reset(docId, layerName, fieldKey) -> DocFormsReset200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().reset(
    "docId",
    "layerName",
    "fieldKey",
    ResetFormsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**fieldKey:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.setValue(docId, layerName, fieldKey, request) -> DocFormsSetValue200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().setValue(
    "docId",
    "layerName",
    "fieldKey",
    SetValueFormsRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**fieldKey:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Metadata
<details><summary><code>client.doc.metadata.get(docId, layerName) -> DocMetadataGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().metadata().get(
    "docId",
    "layerName",
    GetMetadataRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Pages
<details><summary><code>client.doc.pages.delete(docId, layerName, request) -> DocPagesDelete200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().delete(
    "docId",
    "layerName",
    DeletePagesRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.flatten(docId, layerName, request) -> DocPagesFlatten200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().flatten(
    "docId",
    "layerName",
    FlattenPagesRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.move(docId, layerName, request) -> DocPagesMove200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().move(
    "docId",
    "layerName",
    MovePagesRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.rotate(docId, layerName, request) -> DocPagesRotate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().rotate(
    "docId",
    "layerName",
    RotatePagesRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Redactions
<details><summary><code>client.doc.redactions.apply(docId, layerName, request) -> DocRedactionsApply200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().redactions().apply(
    "docId",
    "layerName",
    ApplyRedactionsRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("key", "value");
            }}
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**docId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request:** `Map<String, Object>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

