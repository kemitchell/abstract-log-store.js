# abstract-log-store

## API

### `store.createWriteStream(callback)`

Returns a binary-mode writable stream.

Calls `callback(error, index)` once it writes the message.

`index` is an integer `Number` zero-based index of the message
appended.

### `store.createReadStream(from = 0)`

Returns an object-mode readable stream of messages with indices
greater than or equal to `from`.

Chunks have `.index` and `.stream` properties.

`.index` is an integer `Number`s zero-based index.

`.stream` is a binary-mode readable stream of message data.

If `.createWriteStream()` is used to add messages to the log while a
`.createReadStream()` stream continues, the `.createReadStream()`
stream will _not_ stream the new message.

### `store.length(callback)`

Calls `callback(error, length)`.

`length` is the number of messages in the log.

`index` is an integer `Number` zero-based index of the last message
appended.

### `store.compact(index, callback)`

Calls `callback(error)` once it deletes the data for the message at
the zero-based index `index`.
