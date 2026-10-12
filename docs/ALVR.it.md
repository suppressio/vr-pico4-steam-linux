🌐 [English](ALVR.md) | **Italiano**

# Pico 4 su Linux con ALVR
#### _Guida per usare il visore Pico 4 su Linux, in streaming di software e giochi VR_
***Nota:*** _Questa guida riguarda nello specifico l'uso del software ALVR con il visore Pico 4 per lo streaming di contenuti SteamVR da un sistema Linux basato su Debian._

_Tutte le procedure di installazione descritte sono un compromesso tra passaggi "manuali" e guidati. È uno dei modi possibili per configurare e usare il software._

Qui sotto i requisiti software e i passi per installare e configurare tutto l'ambiente.

## Requisiti software
#### Da installare sul PC (Linux):
- [Steam](https://store.steampowered.com/about/download): serve per SteamVR;
- [SteamVR](https://www.steamvr.com/en/): software gratuito disponibile su Steam. È l'ambiente VR principale sul PC, avvia e gestisce applicazioni e giochi VR. Serve al server ALVR;
- [ALVR Streamer](https://github.com/alvr-org/ALVR): software open source che trasmette i giochi VR dal PC. ALVR Streamer è la parte server. Al momento della stesura l'ultima release è la [20.9.1](https://github.com/alvr-org/ALVR/releases/tag/v20.9.1);

#### Da installare sul Pico 4:
- [ALVR Client](https://github.com/alvr-org/ALVR): la controparte client di ALVR, disponibile come file ".apk";


## Passi di installazione
#### Dal PC:
- [ ] Installa Steam: segui la pagina ufficiale di Debian per [installare Steam](https://wiki.debian.org/Steam#Installing_Steam);
- [ ] Installa SteamVR: apri Steam, cerca SteamVR nello store e installalo;
- [ ] Installa ALVR Streamer: scarica `alvr_streamer_linux.tar.gz` ed estrai l'archivio con i comandi:
```console
mkdir ~/alvr_streamer
tar -xvzf alvr_streamer_linux.tar.gz -C ~/alvr_streamer/
```

- [ ] Avvia ALVR Streamer: nella cartella estratta entra in `bin` e lancia `alvr_dashboard`:
```console
cd ~/alvr_streamer/bin
./alvr_dashboard
```

##### Configura ALVR Streamer (server):
- [ ] Primo avvio:
- Al primo avvio una procedura guidata fa alcuni controlli di sistema e qualche scelta. Premi "Next" fino alla fine.
Nel mio caso, a un certo passo è comparso il messaggio "Unsupported OS" (l'ho ignorato).

![ALVR Wizard Welcome](../resources/images/ALVR-wizard-welcome.png)
![ALVR Wizard Unsupported OS](../resources/images/ALVR-wizard-unsupportedOS.png)

- [ ] Scheda Installation:
- Premi "Register ALVR Driver".

![ALVR Wizard To Register Driver](../resources/images/ALVR-toRegister-driver.png)
![ALVR Wizard Registered Driver](../resources/images/ALVR-registered-driver.png)

- [ ] Scheda Settings, puoi impostare:
Video:
- Preferred framerate: 90Hz;
- Resolution: io ho scelto "Ultra";

![ALVR Video Settings](../resources/images/ALVR-video-settings.png)

- [ ] Scheda Connection:
- Stream protocol: TCP (senza, avevo disconnessioni frequenti);

![ALVR Connection Settings](../resources/images/ALVR-connection-settings.png)

- [ ] Premi "Launch SteamVR"...

##### 💩 succede: riattivare gli add-on di SteamVR:
- [ ] Controlla gli add-on disattivati: a questo punto SteamVR potrebbe partire con gli add-on disattivati (compreso quello di ALVR). Riattivali con "Manage Add-ons", poi imposta "alvr_server" su "On". Premi "Restart SteamVR".

![SteamVR Blocked Addons](../resources/images/steamVR-blocked-addons.png)
![SteamVR Unlock Addons](../resources/images/steamVR-unlock-addons.png)

Gli add-on sono attivi correttamente se sul pulsante non compare nessuna indicazione di add-on bloccati.

![SteamVR Enabled Addons](../resources/images/steamVR-correct_addons.png)

ALVR Streamer ora è pronto e aspetta che un client si colleghi.

##### Dal Pico 4:
Il Pico 4 è un dispositivo Android, quindi ci si può installare quasi qualsiasi app Android. Perciò:
- [ ] Installa l'app ALVR Client:

Apri il browser sul Pico e vai alla pagina `https://github.com/alvr-org/ALVR/releases/tag/v20.9.1`.

- Scarica `alvr_client_android.apk`;

![PICO4 ALVR apk Download](../resources/images/PICO-apk-download.jpg)

**ATTENZIONE! Usa la stessa versione di ALVR Client dell'ALVR Streamer installato.**

- Finito il download, premi Open per installare `alvr_client_android.apk`;

![PICO4 ALVR apk Download](../resources/images/PICO-apk-downloaded.jpg)

![PICO4 ALVR apk Install](../resources/images/PICO-apk-install-confirm.jpg)

- [ ] Primo avvio di ALVR Client:

**ATTENZIONE! Il Pico 4 deve essere collegato alla stessa rete Wi-Fi del PC (stessa sottorete). È consigliata una buona connessione Wi-Fi a 5 GHz.**

- Apri la "Library" del Pico 4, scegli "Unknown" nel menu a sinistra e avvia ALVR Client;

![PICO4 ALVR apk Install](../resources/images/PICO-run-ALVR.jpg)

Una volta dentro, torna al PC per continuare...

![PICO4 ALVR Client Searching for streamer](../resources/images/PICO-ALVRclient-searching.jpg)

##### Di nuovo sul PC:

- [ ] Autorizza il nuovo dispositivo:

- Nella scheda "Devices" di ALVR Streamer ora dovrebbe comparire un nuovo dispositivo da autorizzare (trust);

![ALVR Streamer To Trust Device](../resources/images/ALVR-toTrust-device.png)

![ALVR Streamer Trusted Device](../resources/images/ALVR-trusted-device.png)

##### Di nuovo sul Pico 4:

Se il Pico 4 mostra solo `The streamer will begin soon    Please wait...` troppo a lungo (più di 10-20 secondi), può servire chiudere e riaprire ALVR Client se la connessione non parte.

![ALVR Streamer Waiting](../resources/images/PICO-ALVRclient-waiting.jpg)

Ora... finalmente sei dentro l'ambiente Home di SteamVR! 🎉

![SteamVR Home](../resources/images/SteamVR-finally-inside.jpg)


## Appendice, funzioni facoltative
- [Streaming via USB](ALVR-USB.it.md);


## Risoluzione dei problemi
- Schermo nero: per mesi ho avuto lo schermo nero in ALVR Client sul Pico, per un problema di SteamVR. La soluzione è aggiungere un parametro alle "Launch Options" di SteamVR:
> Aggiungi ~/.local/share/Steam/steamapps/common/SteamVR/bin/vrmonitor.sh %command% alle opzioni di avvio di SteamVR (SteamVR -> Gestisci/clic destro -> Proprietà -> Generali -> Opzioni di avvio).
> Il percorso può cambiare a seconda di dove è installato Steam: in quel caso SteamVR non parte proprio. Se succede, trova il percorso reale in Impostazioni di Steam -> Archiviazione: scegli la posizione con la stella (⭐) e prendi il percorso subito sopra le statistiche di utilizzo. Mettilo davanti a steamapps/common/SteamVR/bin/vrmonitor.sh, e usa questo percorso completo nelle opzioni di avvio di SteamVR al posto dell'altro.
[fonte](https://github.com/alvr-org/ALVR/wiki/Linux-Troubleshooting#black-screen-even-when-steamvr-shows-movement).

- Altri problemi possibili: vedi la [pagina di troubleshooting Linux di ALVR](https://github.com/alvr-org/ALVR/wiki/Linux-Troubleshooting#black-screen-even-when-steamvr-shows-movement);
