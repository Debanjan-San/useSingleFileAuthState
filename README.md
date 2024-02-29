# useSingleFileAuthState
Create a JSON file containing all the credentials and keys for the @whiskeysockets/baileys sessions

## How to connect [@whiskeysockets/baileys](https://github.com/WhiskeySockets/Baileys.git)  using useSingleFileAuthState

The ``@whiskeysockets/baileys`` library previously offered a function for storing credentials in a JSON file. However, this functionality has been removed from the main codebase. Here, we present an alternative implementation of the same functionality as a standalone function, ready for use outside of the original library's context.

``` js
import makeWASocket from '@whiskeysockets/baileys'
import useSingleFileAuthState from './index.js'

// utility function to help save the auth state in a single JSON file
const { state, saveState } = await useMultiFileAuthState('auth_info_baileys')
// will use the given state to connect
// so if valid credentials are available -- it'll connect without QR
const conn = makeWASocket({ auth: state }) 
// this will be called as soon as the credentials are updated
conn.ev.on ('creds.update', saveState)
``` 

If the connection is successful, you will see a QR code printed on your terminal screen, scan it with WhatsApp on your phone and you'll be logged in!
