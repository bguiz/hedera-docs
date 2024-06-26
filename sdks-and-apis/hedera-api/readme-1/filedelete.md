# FileDelete

## FileDeleteTransactionBody

Delete the given file. After deletion, it will be marked as deleted and will have no contents. But information about it will continue to exist until it expires. A list of keys was given when the file was created. All the keys on that list must sign transactions to create or modify the file, but any single one of them can be used to delete the file. Each "key" on that list may itself be a threshold key containing other keys (including other threshold keys).

| Field    | Type                               | Description                                                                                |
| -------- | ---------------------------------- | ------------------------------------------------------------------------------------------ |
| `fileID` | [FileID](../basic-types/fileid.md) | The file to delete. It will be marked as deleted until it expires. Then it will disappear. |
