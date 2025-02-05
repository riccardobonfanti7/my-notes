# Prerequisiti

1. **Computer con Risorse Adeguate**: Assicurati che il tuo computer abbia sufficienti risorse hardware (CPU, RAM e spazio su disco) per eseguire una macchina virtuale.
   
2. **Download di Oracle VirtualBox**: Scarica l'ultima versione di [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads).

3. **File ISO del Sistema Operativo**: Assicurati di avere un file ISO del sistema operativo che desideri installare sulla VM. Puoi scaricare distribuzioni Linux gratuitamente o utilizzare un disco di installazione di Windows.

## Guida per Fedora Server 40

1. **Scaricare iso di Fedora server**.
	[effettua il download per Fedora 40 Server DVD iso](https://fedoraproject.org/server/download)
	
2. **Verificare l’integrità dell’immagine scaricata con Powershell**.
	Apri Powershell su Windows e digita: 	```
	Get-FileHash -Algorithm SHA256 "C:\percorso\file.iso"```
	otterrai un codice HASH
	ora dovrai scaricare il checksum sempre dal link precedente e verificare che il codice HASH generato nella powershell sia identico a quello presente nel checksum.
	Se corrisponde significa che l'immagine ISO è integra, in caso contrario è corrotta e dovrai riscaricare l'immagine ISO.
3. **Pianificare le caratteristiche HW della macchina virtuale (2 * CPU min; 1,5 * RAM min; 2,5 * HDD min)**.
	in base alle caratteristiche del tuo computer effettua questi calcoli per impostarli di seguito sul VirtualBox.
4. Nel VirtualBox vai su archiviazione>clicca sull'icona del disco e **seleziona l'immagine ISO** che hai scaricato in precedenza.
5. Assicurati che **la rete sia abilitata** andando nella sezione Rete.
6. Clicca su **Avvia** per avviare la VM.
7. crea un **account** con usuername e password appena si è avviata la macchina virtuale e crea delle **partizioni**(/tmp , /var , /swap) e formattare ogni partizione (se permesso) in **BTRFS**.
8. Dopo aver finito questo processo, clicca su continua e ti troverai in una CLI, dove dovrai eseguire degli aggiornamenti tramite il comando **sudo dnf update**.


