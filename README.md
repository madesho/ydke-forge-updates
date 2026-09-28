# ydke-forge-updates

Manifest pubblico degli aggiornamenti di **YDKE Forge**.

Questo repository esiste solo per essere letto dall'app. Non contiene codice, non
contiene segreti e non richiede autenticazione: l'app lo interroga per sapere se
c'è una versione nuova, scaricare l'APK e mostrarne le novità.

## `latest.json`

| Campo | Significato |
|---|---|
| `versionName` | Versione dell'app (es. `4.0`) |
| `versionCode` | `versionCode` Android, serve al confronto con la versione installata |
| `changelog` | Note di rilascio in Markdown |
| `apkUrl` | Link HTTPS diretto all'APK |
| `apkSha256` | SHA-256 dell'APK, verificato dopo il download |
| `apkSize` | Dimensione in byte, usata per la barra di avanzamento |
| `releasePageUrl` | Pagina della release, per l'installazione manuale |
| `minVersionCode` | `versionCode` minimo da cui questo manifesto è valido |

## Sicurezza

L'app **non si fida di questo manifest** per decidere se installare un file: un
attaccante che potesse riscrivere questi dati pubblicherebbe anche un hash
falsificato.

Il controllo che decide è un altro, ed è compilato dentro l'app: l'APK scaricato
viene accettato **solo se è firmato con la stessa chiave della versione già
installata**. Solo chi possiede quella chiave può produrre un file valido, quindi
un APK sostitutivo firmato con un'altra chiave viene sempre respinto.

Lo `apkSha256` serve esclusivamente a verificare che il download non sia stato
alterato in transito.

## Aggiornare il manifest

1. Compila la release e calcola `Get-FileHash app-release.apk -Algorithm SHA256`
2. Aggiorna `latest.json` con versione, hash e dimensione
3. Carica l'APK come release asset della tag corrispondente
4. `git push`

La chiave con cui l'app viene firmata deve restare identica per sempre: cambiarla
impedirebbe a tutti gli utenti di aggiornare l'app.
