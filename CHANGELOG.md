# YDKE Forge 4.2

Questa è una versione di manutenzione: non cambia nulla di visibile, serve a rendere l'app più solida e più facile da mantenere.

## Correzioni

**Aggiornamento in-app separato dal resto**
La gestione degli aggiornamenti è stata isolata in un componente dedicato invece di stare dentro il gestore principale dello stato. Non cambia nulla per chi usa l'app: il controllo all'avvio resta silenzioso, la notifica compare solo quando lo chiedi tu e la verifica della firma del file scaricato continua a funzionare come prima.

**Un componente centrale per database e impostazioni**
Prima, ogni avvio dell'app costruiva da capo i componenti di accesso a dati e preferenze. Ora esistono una volta sola: le schermate e il gestore dello stato leggono sempre gli stessi dati.

**Stato inutilizzato rimosso**
Due indicatori che venivano aggiornati ma non mostravano mai nulla all'utente sono stati eliminati. Le notifiche di avanzamento della sincronizzazione passano dal canale già esistente, quindi il comportamento visibile non cambia.

## Pulizia

- Rimosso un file di test rimasto dal modello iniziale di Android Studio e ridati due file di test nomi con il nome di quello che verificano davvero
- Rimosse quattro risorse mai usate
- Aggiunte verifiche automatiche a ogni modifica: compilazione, test, controllo di qualità del codice e ricerca di credenziali tracciate per errore
- Nessuna modifica al database, alle traduzioni, alle carte o al funzionamento offline

## Dettagli tecnici

- Compilazione release ottimizzata
- Nessuna dipendenza aggiunta o rimossa
- Verificato che le tue impostazioni, i tuoi mazzi e il tema restino intatti dopo l'aggiornamento
