## Capabilities

This service can be used to:

- [x] stat
- [x] read
- [x] write
- [x] append
- [x] create_dir
- [x] delete
- [x] copy
- [x] rename
- [x] list
- [ ] ~~scan~~
- [ ] ~~presign~~
- [ ] blocking

## Configuration

- `endpoint`: Set the endpoint for connection
- `root`: Set the work directory for backend, default to `/home/$USER/`
- `user`: Set the login user
- `key`: Set the public key for login
- `known_hosts_strategy`: Set the strategy for known hosts, default to `Strict`
- `enable_copy`: Set whether the remote server has copy-file extension

It doesn't support password login, you can use public key instead.

You can refer to [`SftpBuilder`]'s docs for more information

## Example

### Via Builder

```rust
use anyhow::Result;
use opendal::services::Sftp;
use opendal::Operator;

#[tokio::main]
async fn main() -> Result<()> {
    let mut builder = Sftp::default();

    builder.endpoint("127.0.0.1").user("test").key("test_key");

    let op: Operator = Operator::new(builder)?.finish();
    Ok(())
}
```
