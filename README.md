# secret message
# idea
una chat segreta che ha utenti e stanze con o senza password
ha un API scritto in nodejs e typescript
come database verrà utilizzato un database sqlite3
un framework client che sarà vue
entrambi in questa cartella
Funzionamento -> REST API con vue che renderizza i dati e fa http requests

# servizi
- porta API -> 3000
- porta vuejs -> 8080

# documentazione App vue js
- renderizza le informazioni
- path per l'utent
    - / : L'home del sito
    - /createRoom : per creare una room
    - /joinRoom : per unirti a una room
    - /chat : per la chat vera e propria
    - /chatUserError : entri in /chat senza avere fatto il login

# documentazione servizio REST - API
- ricorda un user con la session
- ha diverse path per fare tutto
    - /login : Fa il login dell'utente
    - /logout : Fa il logout dell'utente
    - /joinRoom : Inserisce un utente in una stanza
    - /createRoom : Crea un stanza con l'utente come capo -> dopo 15 min cancella la stanza
    - /getActiveRoomNumber : Ritorna il numero di stanze attive al momento, per la home

Ha una socket per gestire la chat
la socket è disponibile all'indirizzo /

# documentazione database sqlite3
- Il database è un database sqlite3.
- Contiene diverse tabella al suo interno
    - room : Le room attive al momento
        - roomname : TEXT
        - password : TEXT (sha256)
        - deadline : DATETIME
        - havePassword : INT(2)
    - user : Gli user attivi al momento
        - username : TEXT
        - room : rowId of room