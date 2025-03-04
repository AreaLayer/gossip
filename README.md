# Gossip

Gossip is a desktop client for nostr.

Nostr is "Notes and Other Stuff Transmitted by Relays."

This is pre-alpha code. It is not ready for use.

NOTE: I am reworking this code to use GTK4 because something about Tauri/JavaScript/WebkitGTK
is dog slow. See issue #58. I probably wont be pushing my work into this repo until I'm sure
it's on the right path, so don't fret if this repo seems idle for a while.

## Features

- Asychronous design: No busy waiting, no repeatitive polling, easy on your processor.
- Portable to Linux (Debian, RedHat, Arch) MacOS and Windows
- Talks to as few relays as it needs to to keep up with the people you follow, and doesn't overload them with too heavy of requests.
- Look good in light and dark modes.

## nostr features supported

- Reads and displays type=1 (TextNote) events in a feed sorted by time created.
    - Shows replies under the message they reply to
    - Shows deleted events struck out with red deleted marker.
- Shows people you subscribe to in the Person tab
    - Processes type=0 (Metadata) events to show user information on events in your feed (name, avatar)
    - Lets you subscribe to a person (via public key and relay), but currently requires a restart
- Identity:
    - Lets you generate an ID (private key) and stores that key encrypted under a passphrase, zeroing memory when finished with it where it can.
    - Lets you import an ID (private key)
- Settings: feed chunk size, overlap, autofollow, but these don't work right yet.

## nostr features planned for first alpha release

- [ ] Lets you choose and manage relays you post to
- [ ] Lets you post messages
- [ ] Shows reactions (but maybe not yet react yourself)
- [ ] Lets you 'load more' older posts if you want to look back further

## nostr features planned for subsequent releases

- [ ] Lets you subscribe to a person via a DNS ID (NIP-35)
- [ ] Validates users via NIP-05
- [ ] Lets you react to other people's posts
- [ ] Lets you show events from people you don't follow if they reply to a post you do
- [ ] Lets you mute someone
- [ ] Lets you rank relays
- [ ] Shows links as links
- [ ] Shows images inline (option to wait for your approval)
- [ ] Include a 'client' tag
- [ ] Show the 'client' tag of posts
- [ ] Support "content-warning"
- [ ] Allow browsing of relay-global events of people you dont follow
- [ ] Multiple identities
- [ ] Publish your following list
- [ ] Follow someone privately (without including in your posted following list)
- [ ] Allow viewing of other people's following lists w/ petnames
- [ ] Dismiss a message for this session only w/o deleting it

## Technology Involved

- Tauri App Framework
- Rust Language
- HTML and Javascript
- VueJS 3.x (Composition API)
- Vue-Router
- Pinia (Javascript global data storage)
- Vite (for development)
- Yarn (for development)
- SQLite 3
- Tungstenite websocket library
- Tokio async task runtime
- Serde serialization/deserialization
- Many others: (dirs, env_logger, futures, lazy_static, log, nostr-proto, rusqlite, serde_json, textnonce, thiserror)

## License

 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, shall be licensed as above, without any additional
terms or conditions.
