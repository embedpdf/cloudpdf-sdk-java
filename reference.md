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

<details><summary><code>client.doc.changes(docId, layerName, request) -> DocChanges200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Each change stands on its own and names itself by `opId`: a refused change rolls back alone, and the answer lists every change in order, applied with its result or refused with its error. Asked again under its `opId`, a change gets the same answer, refusals included; a different change under an answered `opId` is refused (IdempotencyKeyReused). `{ opId, undoOf }` undoes an earlier change of the caller, here or in an earlier request; an undo leaves alone what was changed since, and the undo of an undo redoes. A redaction, a flatten, a form repair or a completed signature ends undo for the changes before it (UndoUnavailable). Each op is checked against its own capability: annotation ops need `doc.annotate.modify`, form values `doc.forms.fill`, form structure `doc.forms.modify`, metadata `doc.metadata.modify`, outline `doc.outline.modify`, pages `doc.pages.assemble`, embedded files `doc.attachments.modify`. Bytes (a stamp's drawing, an attached file, a signature's artwork, a PDF whose pages come in) travel as multipart: a JSON `body` part, each op naming its files by role as `resources: { <role>: '<key>' }`, and each file as the part `resource:<key>`. At most 64 changes per request and 512 ops per change.
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
client.doc().changes(
    "docId",
    "layerName",
    DocChangesRequest
        .builder()
        .changes(
            Arrays.asList(
                DocChangesRequestChangesItem
                    .builder()
                    .opId("opId")
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

**changes:** `List<DocChangesRequestChangesItem>` 
    
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

<details><summary><code>client.doc.downloadLink(docId, layerName, request) -> DocDownloadLink200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The link opens the layer as it is when created: once the layer changes, it answers 404, so create it right before handing it over. It downloads that one file and nothing else, and a password-protected document is checked when the link is created. Deployments that verify tokens with their own keys (JWKS) mint links on their backend: a doc token with `layer_name`, a `download: { docVersion, mode: "incremental" }` claim and a short `exp`, passed as `link` on the versioned download URL.
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
client.doc().downloadLink(
    "docId",
    "layerName",
    DocDownloadLinkRequest
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

<dl>
<dd>

**expiresIn:** `Optional<Integer>` 
    
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

<details><summary><code>client.doc.render(docId, layerName, pageKey) -> InputStream</code></summary>
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
    "pageKey",
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

<details><summary><code>client.doc.text(docId, layerName, pageKey) -> DocText200Response</code></summary>
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
    "pageKey",
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

Unauthenticated, but requires a browser Origin header, checked against the grant allowlist. Unknown, revoked, and disabled tokens are indistinguishable (404). Passphrase-protected grants return 422 SharePasswordRequired until `password` is supplied. A link that asks its visitors who they are on open returns 422 VisitorIdentityRequired until the required answers are given; `error.details` carries `fields` (what the link asks), `missing`, `invalid`, `purpose` and `privacyUrl`. A link that asks before the first change issues the session at once with `visitor.identityRequest`, and writes answer 403 VisitorIdentityRequired with the same details until the visitor exchanges again with their answers. Answers that can not be taken answer 422 on any link. Mounted only when the deployment can sign (HS256 mode).
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

<dl>
<dd>

**visitorHandle:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**restart:** `Optional<Boolean>` 
    
</dd>
</dl>

<dl>
<dd>

**visitorIdentity:** `Optional<SharesExchangeRequestVisitorIdentity>` 
    
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

<dl>
<dd>

**archived:** `Optional<Boolean>` 
    
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

The returned share id is the public share token. Mounted only when the deployment can sign (HS256 mode) — exchange mints session JWTs, so grants exist only where minting does.
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

**layerMode:** `Optional<SharesCreateRequestLayerMode>` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**keepVisitorLayers:** `Optional<Boolean>` 
    
</dd>
</dl>

<dl>
<dd>

**visitorIdleSeconds:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**visitorIdentity:** `Optional<SharesCreateRequestVisitorIdentity>` 
    
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

**layerMode:** `Optional<SharesUpdateRequestLayerMode>` 
    
</dd>
</dl>

<dl>
<dd>

**layerName:** `Optional<String>` 
    
</dd>
</dl>

<dl>
<dd>

**keepVisitorLayers:** `Optional<Boolean>` 
    
</dd>
</dl>

<dl>
<dd>

**visitorIdleSeconds:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**visitorIdentity:** `Optional<SharesUpdateRequestVisitorIdentity>` 
    
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

<details><summary><code>client.shares.archive(tenantId, shareId) -> SharesArchive200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Archiving is final: an archived link never exchanges again, and to share again you create a new link. Pausing (`disabled`) is the reversible stop. An archived link no longer counts as using its shared layer, so that layer can be deleted.
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
client.shares().archive(
    "tenantId",
    "shareId",
    ArchiveSharesRequest
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

**source:** `DocumentsImportFromRequestSource` — Where CloudPDF pulls the bytes from. The two shapes differ in who supplies the authority to read, not in which storage vendor holds the file.
    
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
<details><summary><code>client.doc.annotations.listAll(docId, layerName) -> AnnotationList</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns one entry per page plus the audit-log cursor for reconciling subsequent document events. Page order is unspecified; join by `page` (a `PageRef`) when display order matters.
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
client.doc().annotations().listAll(
    "docId",
    "layerName",
    ListAllAnnotationsRequest
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

<details><summary><code>client.doc.annotations.list(docId, layerName, pageKey) -> AnnotationList</code></summary>
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
    "pageKey",
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

<details><summary><code>client.doc.annotations.create(docId, layerName, pageKey, request) -> DocAnnotationsCreate200Response</code></summary>
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
    "pageKey",
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.annotations.delete(docId, layerName, pageKey, annotKey) -> DocAnnotationsDelete200Response</code></summary>
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
    "pageKey",
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.update(docId, layerName, pageKey, annotKey, request) -> DocAnnotationsUpdate200Response</code></summary>
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
    "pageKey",
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.annotations.readAppearance(docId, layerName, pageKey, annotKey) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().readAppearance(
    "docId",
    "layerName",
    "pageKey",
    "annotKey",
    ReadAppearanceAnnotationsRequest
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
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

<details><summary><code>client.doc.annotations.readFile(docId, layerName, pageKey, annotKey) -> InputStream</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A file that decodes past the server's limit is refused (PayloadTooLarge).
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
client.doc().annotations().readFile(
    "docId",
    "layerName",
    "pageKey",
    "annotKey",
    ReadFileAnnotationsRequest
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
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

<details><summary><code>client.doc.annotations.exportAppearance(docId, layerName, pageKey, request) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().exportAppearance(
    "docId",
    "layerName",
    "pageKey",
    ExportAppearanceAnnotationsRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("string", new 
                HashMap<String, Object>() {{put("key", "value");
                }});
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

<details><summary><code>client.doc.annotations.flatten(docId, layerName, pageKey, request) -> DocAnnotationsFlatten200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().flatten(
    "docId",
    "layerName",
    "pageKey",
    FlattenAnnotationsRequest
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.annotations.reorder(docId, layerName, pageKey, request) -> DocAnnotationsReorder200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().annotations().reorder(
    "docId",
    "layerName",
    "pageKey",
    DocAnnotationsReorderRequest
        .builder()
        .position(
            AnnotationPosition.of(AnnotationPositionZero.START)
        )
        .refs(
            Arrays.asList(
                AnnotationRef.objectNumber(
                    AnnotationRefObjectNumber
                        .builder()
                        .page(
                            PageRef
                                .builder()
                                .kind(PageRefKind.OBJECT_NUMBER)
                                .objectNumber(1)
                                .build()
                        )
                        .objectNumber(1)
                        .build()
                )
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**refs:** `List<AnnotationRef>` 
    
</dd>
</dl>

<dl>
<dd>

**position:** `AnnotationPosition` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Attachments
<details><summary><code>client.doc.attachments.download(docId, layerName, fileKey) -> InputStream</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A file that decodes past the server's limit is refused (PayloadTooLarge).
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
client.doc().attachments().download(
    "docId",
    "layerName",
    "fileKey",
    DownloadAttachmentsRequest
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

**fileKey:** `String` — The embedded file's name-tree key (its `ref.key`), token-text encoded, as `fieldKey` is.
    
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

<details><summary><code>client.doc.attachments.list(docId, layerName) -> AttachmentList</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A file-attachment annotation's file is listed with the annotation; read its bytes with `doc.annotations.readFile`.
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
client.doc().attachments().list(
    "docId",
    "layerName",
    ListAttachmentsRequest
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

## Doc Forms
<details><summary><code>client.doc.forms.list(docId, layerName) -> DocFormsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().list(
    "docId",
    "layerName",
    ListFormsRequest
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

<details><summary><code>client.doc.forms.reorderCalculations(docId, layerName, request) -> DocFormsReorderCalculations200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().reorderCalculations(
    "docId",
    "layerName",
    DocFormsReorderCalculationsRequest
        .builder()
        .position(
            FieldPosition.of(FieldPositionZero.START)
        )
        .fields(
            Arrays.asList(
                FormFieldRef.objectNumber(
                    FormFieldRefObjectNumber
                        .builder()
                        .objectNumber(1)
                        .build()
                )
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

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `List<FormFieldRef>` 
    
</dd>
</dl>

<dl>
<dd>

**position:** `FieldPosition` 
    
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

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.forms.reset(docId, layerName, request) -> DocFormsReset200Response</code></summary>
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
    DocFormsResetRequest
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

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**refs:** `Optional<List<FormFieldRef>>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.deleteWidget(docId, layerName, pageKey, annotKey) -> DocFormsDeleteWidget200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().deleteWidget(
    "docId",
    "layerName",
    "pageKey",
    "annotKey",
    DeleteWidgetFormsRequest
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.updateWidget(docId, layerName, pageKey, annotKey, request) -> DocFormsUpdateWidget200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().updateWidget(
    "docId",
    "layerName",
    "pageKey",
    "annotKey",
    DocFormsUpdateWidgetRequest
        .builder()
        .patch(
            WidgetPatch
                .builder()
                .build()
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annotKey:** `String` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**patch:** `WidgetPatch` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.reorderWidgets(docId, layerName, pageKey, request) -> DocFormsReorderWidgets200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().forms().reorderWidgets(
    "docId",
    "layerName",
    "pageKey",
    DocFormsReorderWidgetsRequest
        .builder()
        .position(
            AnnotationPosition.of(AnnotationPositionZero.START)
        )
        .widgets(
            Arrays.asList(
                AnnotationRef.objectNumber(
                    AnnotationRefObjectNumber
                        .builder()
                        .page(
                            PageRef
                                .builder()
                                .kind(PageRefKind.OBJECT_NUMBER)
                                .objectNumber(1)
                                .build()
                        )
                        .objectNumber(1)
                        .build()
                )
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**widgets:** `List<AnnotationRef>` 
    
</dd>
</dl>

<dl>
<dd>

**position:** `AnnotationPosition` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Metadata
<details><summary><code>client.doc.metadata.get(docId, layerName) -> DocumentMetadata</code></summary>
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

## Doc Outline
<details><summary><code>client.doc.outline.get(docId, layerName) -> DocumentOutline</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().outline().get(
    "docId",
    "layerName",
    GetOutlineRequest
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
<details><summary><code>client.doc.pages.setScale(docId, layerName, pageKey, request) -> DocPagesSetScale200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().setScale(
    "docId",
    "layerName",
    "pageKey",
    DocPagesSetScaleRequest
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**measure:** `Optional<DocPagesSetScaleRequestMeasure>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.viewports(docId, layerName, pageKey) -> DocPagesViewports200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().viewports(
    "docId",
    "layerName",
    "pageKey",
    ViewportsPagesRequest
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

**pageKey:** `String` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

<details><summary><code>client.doc.pages.extract(docId, layerName, request) -> InputStream</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A read, not a mutation: the source document is untouched and no event is published. Body is `{"pages": PageRef[], "flatten"?: {"usage"?: "display" | "print"}, "includeAnnotations"?: boolean, "includeFormFields"?: boolean}`; the response body is the new PDF. With `flatten` the copy is the pages as they draw for `usage` (`"print"`: a print copy): the annotations and form fields painted in, nothing interactive left, layers in their state for the usage. A flattened copy takes `doc.download` or `doc.download.flattened`, and paints only what the caller may read; `includeAnnotations` and `includeFormFields` choose what it paints, and are refused without `flatten`.
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
client.doc().pages().extract(
    "docId",
    "layerName",
    ExtractPagesRequest
        .builder()
        .body(
            new HashMap<String, Object>() {{
                put("string", new 
                HashMap<String, Object>() {{put("key", "value");
                }});
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

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.pages.setName(docId, layerName, request) -> DocPagesSetName200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().setName(
    "docId",
    "layerName",
    SetNamePagesRequest
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

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.pages.removeName(docId, layerName, request) -> DocPagesRemoveName200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().pages().removeName(
    "docId",
    "layerName",
    RemoveNamePagesRequest
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

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
    DocRedactionsApplyRequest
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

<dl>
<dd>

**idempotencyKey:** `Optional<String>` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**pages:** `Optional<List<PageRef>>` 
    
</dd>
</dl>

<dl>
<dd>

**annotations:** `Optional<List<AnnotationRef>>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Signatures
<details><summary><code>client.doc.signatures.list(docId, layerName) -> DocSignaturesList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Describes the bytes the layer is over: the base version's signatures plus the layer's own edits as the last revision. Signed bytes (contents, digests, revision prefixes) are served per base version under /versions.
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
client.doc().signatures().list(
    "docId",
    "layerName",
    ListSignaturesRequest
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

<details><summary><code>client.doc.signatures.cancel(docId, layerName, signingId) -> DocSignaturesCancel200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().signatures().cancel(
    "docId",
    "layerName",
    "signingId",
    CancelSignaturesRequest
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

**signingId:** `String` 
    
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

<details><summary><code>client.doc.signatures.complete(docId, layerName, signingId, request) -> DocSignaturesComplete200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

`cms` is the detached CMS over the prepared digest, base64. `expectedVersion` must be what prepare returned. Idempotent by signing id: the same CMS again answers `already-completed`. Every layer of the document then sits over the new version; refetch the manifest after a completion.
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
client.doc().signatures().complete(
    "docId",
    "layerName",
    "signingId",
    DocSignaturesCompleteRequest
        .builder()
        .cms("cms")
        .expectedVersion(
            DocSignaturesCompleteRequestExpectedVersion
                .builder()
                .baseSha256("baseSha256")
                .editsVersion(1)
                .build()
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

**signingId:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**documentPassword:** `Optional<String>` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**cms:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**expectedVersion:** `DocSignaturesCompleteRequestExpectedVersion` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.signatures.analysis(docId, layerName) -> DocSignaturesAnalysis200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Exactly one of `since.signature=<index>` or `since.revision=<index>`; the layer's pending edits are the end. `level=fill|annotate|lta|none` evaluates exploratorily and never becomes a verdict. For history between two base revisions use the version analysis.
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
client.doc().signatures().analysis(
    "docId",
    "layerName",
    AnalysisSignaturesRequest
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

**sinceSignature:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**sinceRevision:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**level:** `Optional<AnalysisSignaturesRequestLevel>` 
    
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

<details><summary><code>client.doc.signatures.prepare(docId, layerName, request) -> DocSignaturesPrepare200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Multipart: a JSON `body` part (field, subFilter, digest, contentsSize, signer, certify, lock), naming the appearance PDF it may carry as `resources: { appearance: '<key>' }`, and that PDF as the part `resource:<key>`. A certification (`certify.permission`) additionally requires `doc.sign.certify`. The layer is read-only until the signing completes, is cancelled, or expires (15 minutes). A layer behind the document head cannot sign (StaleBase).
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
client.doc().signatures().prepare(
    "docId",
    "layerName",
    null,
    PrepareSignaturesRequest
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

## Doc Versions
<details><summary><code>client.doc.versions.list(docId) -> DocVersionsList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every completed signature publishes a new version. Never cached: the list grows.
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
client.doc().versions().list(
    "docId",
    ListVersionsRequest
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

<details><summary><code>client.doc.versions.analysis(docId, sha) -> DocVersionsAnalysis200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Exactly one of `since.signature` / `since.revision`; `until=<revision>` defaults to the last. The same answer for every layer and every caller.
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
client.doc().versions().analysis(
    "docId",
    "sha",
    AnalysisVersionsRequest
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

**sha:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**sinceSignature:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**sinceRevision:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**level:** `Optional<AnalysisVersionsRequestLevel>` 
    
</dd>
</dl>

<dl>
<dd>

**until:** `Optional<Integer>` 
    
</dd>
</dl>

<dl>
<dd>

**policy:** `Optional<Integer>` 
    
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

<details><summary><code>client.doc.versions.download(docId, sha) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().versions().download(
    "docId",
    "sha",
    DownloadVersionsRequest
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

**sha:** `String` 
    
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

<details><summary><code>client.doc.versions.revision(docId, sha, index) -> InputStream</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().versions().revision(
    "docId",
    "sha",
    1,
    RevisionVersionsRequest
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

**sha:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**index:** `Integer` 
    
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

<details><summary><code>client.doc.versions.signatures(docId, sha) -> DocVersionsSignatures200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().versions().signatures(
    "docId",
    "sha",
    SignaturesVersionsRequest
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

**sha:** `String` 
    
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

<details><summary><code>client.doc.versions.signatureContents(docId, sha, fieldKey) -> InputStream</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

`fieldKey` is the field's fully qualified name, token-text encoded (the same encoding attachment keys use).
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
client.doc().versions().signatureContents(
    "docId",
    "sha",
    "fieldKey",
    SignatureContentsVersionsRequest
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

**sha:** `String` 
    
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

<details><summary><code>client.doc.versions.signatureDigest(docId, sha, fieldKey, algorithm) -> InputStream</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

What a CMS verifier compares its message digest to.
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
client.doc().versions().signatureDigest(
    "docId",
    "sha",
    "fieldKey",
    SignatureDigestVersionsRequestAlgorithm.SHA1,
    SignatureDigestVersionsRequest
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

**sha:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**fieldKey:** `String` 
    
</dd>
</dl>

<dl>
<dd>

**algorithm:** `SignatureDigestVersionsRequestAlgorithm` 
    
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

## Doc Metadata Custom
<details><summary><code>client.doc.metadata.custom.get(docId, layerName) -> Map&amp;lt;String, String&amp;gt;</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.doc().metadata().custom().get(
    "docId",
    "layerName",
    GetCustomRequest
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

## Documents Layers
<details><summary><code>client.documents.layers.list(tenantId, id) -> DocumentsLayersList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().layers().list(
    "tenantId",
    "id",
    ListLayersRequest
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

**shareId:** `Optional<String>` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.layers.delete(tenantId, id, layerName)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.documents().layers().delete(
    "tenantId",
    "id",
    "layerName",
    DeleteLayersRequest
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

<dl>
<dd>

**layerName:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Shares Visitors
<details><summary><code>client.shares.visitors.list(tenantId, shareId) -> SharesVisitorsList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

An archived link's visitors are listed too.
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
client.shares().visitors().list(
    "tenantId",
    "shareId",
    ListVisitorsRequest
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

<details><summary><code>client.shares.visitors.delete(tenantId, shareId, visitorId)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Their handle brings them back as a new visitor, who is asked again. Deleting a visitor already deleted changes nothing.
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
client.shares().visitors().delete(
    "tenantId",
    "shareId",
    "visitorId",
    DeleteVisitorsRequest
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

**visitorId:** `String` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

