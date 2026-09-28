# YDKE Forge 4.0

## Importante: come installare questa versione

Questa release **non si può installare sopra la 3.8.3**.

Due motivi, entrambi legati alla sicurezza:

1. **L'app è firmata con una chiave nuova.** Le versioni precedenti erano firmate con la chiave di debug di Android, la cui chiave privata è pubblica e identica su ogni computer al mondo: chiunque poteva firmare un file che il sistema accettava come aggiornamento legittimo dell'app. Ora la chiave è tua e custodita al sicuro.
2. **Il nome del pacchetto è cambiato** da `com.aistudio.ydkeforge.krwv` a `com.madesho.ydkeforge`.

Per passare a questa versione devi **disinstallare la 3.8.3 e installare questa da zero**. Perderai i mazzi salvati e la cache delle carte già scaricate, che verranno riscaricate automaticamente al primo avvio. Le impostazioni (tema, lingua, preferenze) vanno reimpostate.

Questo vale per la 4.0 e non si ripeterà: dalla 4.1 in poi l'aggiornamento avverrà dall'app.

## Aggiornamento in-app più sicuro

- L'aggiornamento non usa più alcun token di accesso. Le credenziali non sono più necessarie per aggiornare l'app e non sono più presenti dentro l'APK.
- Prima di installare, l'app **verifica** che il file scaricato corrisponda all'hash annunciato e, soprattutto, che sia **firmato con la stessa chiave dell'app già installata**. Un file firmato con un'altra chiave viene rifiutato anche se il sito che lo distribuisce fosse compromesso.
- Se l'hash o la firma non corrispondono, l'installazione non parte e ricevi un avviso.

## Correzioni

**Visualizzatore mazzo: eliminato lo spazio nero sopra l'header**
L'area di stato veniva applicata due volte all'header del deck, lasciando una fascia nera tra il nome del mazzo e la barra di ricerca.

**Visualizzatore carte a schermo intero: rispetta il tema scelto**
L'apertura a schermo intero ripartiva sempre dai colori di fabbrica e ignorava le preferenze. Ora segue il tema impostato: nero puro con AMOLED attivo, fondo chiaro in modalità chiara, con le icone delle barre di sistema sempre leggibili.

**Ritorno della carta esattamente nella posizione di partenza**
Chiudendo la vista a schermo intero la carta tornava nella posizione sbagliata, e lo scarto aumentava scorrendo il dettaglio. Ora torna sempre sulla miniatura di origine.

**Zoom graduale in ingresso e in uscita**
Lo sfondo compariva di colpo mentre la carta era già a metà percorso. Ora sfondo e zoom si muovono insieme, senza immagini fantasma.

**Titolo delle carte dinamiche centrato sulle maiuscole**
Il nome della carta era leggermente storto in verticale rispetto alle maiuscole stampate sulla carta fisica.

**Barra di ricerca e badge coerenti con il tema**
Con il tema chiaro impostato su un sistema scuro (o con AMOLED attivo) la barra di ricerca restava grigio scuro e i badge delle tipologie di carta ignoravano la scelta. Ora leggono il tema effettivamente attivo.

**Pulsanti coerenti con il tema attivo**
I pulsanti di Copia, Codice QR, Condividi e quelli della carta convertita avevano colori fissi: restavano dorati, viola o rossi anche con un tema diverso. Ora usano i colori del tema selezionato.

**Nessun flash bianco all'avvio in scuro**
Su tema scuro e AMOLED compariva una schermata bianca prima che l'app si colorasse.

**I tuoi dati non finiscono più nel backup**
Il database con le carte e i tuoi mazzi salvati veniva incluso nel backup automatico di Google e nel trasferimento tra dispositivi. Ora sono esclusi.

## Pulizia

- Rimossi 5 componenti di rete che non erano usati (nessun effetto sul funzionamento, build più veloce e meno superficie esposta).
- Corretto un test che interrogava un sito esterno e faceva fallire la verifica automatica senza connessione.
- Le regole di ottimizzazione del codice ora conservano nomi di file e numeri di riga negli errori: gli avvisi di crash della release sono finalmente leggibili.

## Dettagli tecnici

- Compilazione release ottimizzata
- Firma con chiave dedicata; la build fallisce se la chiave non è configurata, senza ripiegare su chiavi di debug
- Nessuna modifica al funzionamento offline e al catalogo: tutte le API restano raggiungibili come prima
