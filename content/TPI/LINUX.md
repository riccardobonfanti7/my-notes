# GUIDA COMANDI 

>La shell più comunemente utilizzata per i [[SO]] Linux è chiamata shell Bash([[CLI]]).

Il ~ simbolo viene utilizzato come abbreviazione per la directory home dell'utente. 

In questa guida potrai trovare i comandi fondamentali di Linux con i relativi esempi e spiegazioni di ciò che avviene.

**comando [opzioni] [argomenti]**

___

  

**pwd** [OPTIONS]

Il comando pwd <u>stampa la directory di lavoro</u>, che è la posizione corrente dell'utente all'interno del filesystem.

```

sysadmin@localhost:~$ pwd

/home/sysadmin

```

___

**cd** [options] [path]

Per navigare nel filesystem, usa **cd** command.

```

sysadmin@localhost:~$ cd Documents

sysadmin@localhost:~/Documents$

```

  

Il carattere ~ è equivalente a /home/sysadmin, che rappresenta la directory home dell'utente.

  

Se utilizzato senza argomenti, il comando cd porterà l'utente alla propria directory home.

```

sysadmin@localhost:~/Documents$ cd

sysadmin@localhost:~$

```

Puoi mettere anche un percorso di tipo assoluto utilizzando il comando cd:

```

sysadmin@localhost:~/Documents$ cd /home/sysadmin/Documents/School/Art

sysadmin@localhost:~/Documents/School/Art$

```

Due caratteri punto **..** rappresentano sempre una directory più in alto rispetto alla directory corrente.

```

sysadmin@localhost:~/Documents/School/Art$ cd ..

sysadmin@localhost:~/Documents/School$

```

___

ls [OPTION]... [FILE]...

Questo comando **ls** viene utilizzato per visualizzare il contenuto di una directory e può fornire informazioni dettagliate sui file.

```

sysadmin@localhost:~$ ls

Desktop Documents Downloads Music Pictures Public

```

Il comando **ls** può essere utilizzato anche <u>per elencare il contenuto di qualsiasi directory nel filesystem</u>. Fornire il percorso della directory come argomento:

```

sysadmin@localhost:~$ ls /var

backups cache lib local lock log mail opt run spool tmp

```

Il comando ls <u>omette i file nascosti</u> per impostazione predefinita. Un file nascosto è qualsiasi file (o directory) che inizia con un punto(.) carattere.

```

sysadmin@localhost:~$ ls -a

. .bashrc .selected_editor Downloads Public

.. .cache Desktop Music Templates

.bash_logout .profile Documents Pictures Videos

```

A ogni file sono associati dettagli chiamati [[metadati]].

Per visualizzare queste informazioni, utilizzare ** l'opzione -l** del comando ls.

```

sysadmin@localhost:~$ ls -l /var/log/

total 900

-rw-r--r-- 1 root root 15322 Dec 10 21:33 alternatives.log

drwxr-xr-x 1 root root 4096 Jul 19 06:52 apt

-rw-r----- 1 syslog adm 371 Dec 15 16:38 auth.log

-rw-r--r-- 1 root root 35330 May 26 2018 bootstrap.log

-rw-rw---- 1 root utmp 0 May 26 2018 btmp

-rw-r----- 1 syslog adm 197 Dec 15 16:38 cron.log

-rw-r--r-- 1 root adm 85083 Dec 10 21:33 dmesg

-rw-r--r-- 1 root root 351960 Jul 19 06:52 dpkg.log

-rw-r--r-- 1 root root 32064 Dec 10 21:33 faillog

drwxr-xr-x 2 root root 4096 Jul 19 06:51 journal

-rw-rw-r-- 1 root utmp 292584 Dec 15 16:38 lastlog

-rw-r----- 1 syslog adm 14185 Dec 15 16:38 syslog

-rw------- 1 root root 64128 Dec 10 21:33 tallylog

-rw-rw-r-- 1 root utmp 384 Dec 15 16:38 wtmp

```

```

sysadmin@localhost:~$ ls -ld

drwxr-xr-x 1 sysadmin sysadmin 224 Nov 7 17:07 .

```

___
Per eseguire un elenco ricorsivo, utilizzare **l'opzione -R** del comando ls:

```

sysadmin@localhost:~$ ls -R /etc/ppp

/etc/ppp:

ip-down.d ip-up.d

  

/etc/ppp/ip-down.d:

bind9

  

/etc/ppp/ip-up.d:

bind9

```

___
Per ordinare i file in base alla dimensione, possiamo utilizzare **l'opzione -S**.

```

sysadmin@localhost:~$ ls -S /etc/ssh

moduli ssh_host_ed25519_key ssh_host_ecdsa_key.pub

sshd_config ssh_host_rsa_key.pub ssh_host_ed25519_key.pub

ssh_host_rsa_key ssh_import_id

ssh_config ssh_host_ecdsa_key

```

Potrebbe anche essere utile utilizzare **l'opzione -h** per visualizzare le dimensioni dei file leggibili dall'uomo.

  

**L'opzione -t** ordina i file in base all'ora in cui sono stati modificati.


# Command Line Pipes




Il comando `ls /etc | head` in Linux esegue due comandi concatenati tramite una pipeline (`|`). 

Ecco cosa fanno:

1. **`ls /etc`**: Questo elenca il contenuto della directory `/etc`, che solitamente contiene file di configurazione del sistema.
2. **`head`**: Questo legge e mostra solo le prime dieci righe dell'output che riceve dal comando precedente.

Il comando `ls /etc/ssh | nl` in Linux esegue due operazioni concatenate tramite una pipeline (`|`). Ecco cosa succede:

1. **`ls /etc/ssh`**: Questo elenca il contenuto della directory `/etc/ssh`, che contiene file di configurazione per il server SSH.
2. **`nl`**: Questo comando prende l'output ricevuto dal comando precedente e aggiunge numeri di riga a ciascuna linea di testo.

```shell
     1    ssh_config
     2    sshd_config
     3    moduli
     4    ssh_host_rsa_key
     5    ssh_host_ecdsa_key
     6    ssh_host_ed25519_key
```



Il comando `ls /etc/ssh | nl | tail -5` esegue tre operazioni concatenate tramite pipeline (`|`). Ecco cosa fanno:

1. **`ls /etc/ssh`**: Questo elenca il contenuto della directory `/etc/ssh`, che contiene file di configurazione per il server SSH.
2. **`nl`**: Questo comando aggiunge numeri di riga a ciascuna linea di testo dell'output del comando precedente.
3. **`tail -5`**: Questo legge e mostra solo le ultime cinque righe dell'output che riceve.

```shell
     5    ssh_host_ed25519_key
     6    ssh_host_rsa_key
     7    ssh_host_ecdsa_key
     8    ssh_host_ed25519_key.pub
     9    ssh_host_rsa_key.pub
```


Il comando `ls /etc/ssh | tail -5 | nl` esegue tre operazioni concatenate tramite pipeline (`|`). Ecco cosa fanno:

1. **`ls /etc/ssh`**: Questo elenca il contenuto della directory `/etc/ssh`, che contiene file di configurazione per il server SSH.
2. **`tail -5`**: Questo legge e mostra solo le ultime cinque righe dell'output che riceve.
3. **`nl`**: Questo comando aggiunge numeri di riga a ciascuna linea di testo dell'output del comando precedente.

```shell
     1    ssh_host_rsa_key
     2    ssh_host_ecdsa_key
     3    ssh_host_ed25519_key
     4    ssh_host_rsa_key.pub
     5    ssh_host_ecdsa_key.pub
```

### STDIN (Standard Input)

- Informazioni inserite normalmente dall'utente tramite la tastiera.
- Quando un comando richiede dati, la shell consente all'utente di digitare i comandi, che vengono inviati al comando come STDIN.

### STDOUT (Standard Output)

- Output normale dei comandi.
- Quando un comando funziona correttamente (senza errori), l'output prodotto è chiamato STDOUT.
- Di default, STDOUT è visualizzato nella finestra del terminale dove il comando è in esecuzione.
- Conosciuto anche come stream o canale #1.

### STDERR (Standard Error)

- Messaggi di errore generati dai comandi.
- Di default, STDERR è visualizzato nella finestra del terminale dove il comando è in esecuzione.
- Conosciuto anche come stream o canale #2.

## STDOUT

Quando usi il carattere `>`, l'output del comando viene inviato a un file invece che allo schermo. In questo caso:

```shell
sysadmin@localhost:~$ echo "Line 1" > example.txt
```

Il testo "Line 1" viene scritto nel file `example.txt`. Il comando non mostra alcun output sullo schermo perché tutto è stato rediretto nel file. Puoi verificare che il file sia stato creato usando il comando `ls`, come hai fatto:

```shell
sysadmin@localhost:~$ ls
Desktop    Downloads  Pictures  Templates  example.txt
Documents  Music      Public    Videos
```

simbolo `>` sovrascrive il contenuto esistente del file, mentre usare `>>` aggiunge il nuovo contenuto alla fine del file, preservando quello che già c'era. Ecco un riepilogo rapido:

1. **Sovrascrivere un file esistente**:
    ```shell
    sysadmin@localhost:~$ echo "New line 1" > example.txt
    ```

2. **Aggiungere contenuto a un file esistente**:
    ```shell
    sysadmin@localhost:~$ echo "Another line" >> example.txt
    ```

Utilizzando `cat example.txt` puoi verificare il contenuto del file in ogni fase:

```shell
sysadmin@localhost:~$ cat example.txt
New line 1
Another line
```




1. **Comando e errore**:
    ```shell
    sysadmin@localhost:~$ ls /fake
    ls: cannot access /fake: No such file or directory
    ```
    Questo errore indica che la directory `/fake` non esiste. Anche se l'output è chiaramente un messaggio di errore, non c'è alcun indizio implicito che venga inviato a STDERR.

2. **Redirezione di STDOUT**:
    ```shell
    sysadmin@localhost:~$ ls /fake > output.txt
    ls: cannot access /fake: No such file or directory
    ```
    Qui, STDOUT è rediretto a `output.txt`. Poiché l'errore viene ancora mostrato sul terminale, si può concludere che è stato inviato a STDERR.

3. **Redirezione di STDERR**:
    ```shell
    sysadmin@localhost:~$ ls /fake 2> error.txt
    ```
    In questo esempio, `2>` indica che tutti i messaggi di errore devono essere inviati a `error.txt`.

4. **Verifica del file di errore**:
    ```shell
    sysadmin@localhost:~$ cat error.txt
    ls: cannot access /fake: No such file or directory
    ```
    Usando `cat error.txt`, puoi confermare che i messaggi di errore sono stati inviati correttamente al file `error.txt`.



**STDERR** può essere rediretto in modo simile a **STDOUT**. Quando si utilizza il carattere `>`, per impostazione predefinita viene rediretto lo stream #1 (STDOUT), a meno che non venga specificato un altro stream. Pertanto, per redirigere STDERR, lo stream #2 deve essere specificato anteponendo il numero 2 al carattere `>`.

### Esempio di redirezione di STDERR

1. **Comando che genera un errore**:
    ```shell
    sysadmin@localhost:~$ ls /fake
    ls: cannot access /fake: No such file or directory
    ```
    Questo comando produce un errore perché la directory `/fake` non esiste. Il messaggio di errore non implica chiaramente che viene inviato a STDERR.

2. **Redirezione di STDOUT**:
    ```shell
    sysadmin@localhost:~$ ls /fake > output.txt
    ls: cannot access /fake: No such file or directory
    ```
    In questo esempio, STDOUT è stato rediretto al file `output.txt`. Poiché l'errore viene ancora visualizzato sul terminale, si può concludere che è stato inviato a STDERR.

3. **Redirezione di STDERR**:
    ```shell
    sysadmin@localhost:~$ ls /fake 2> error.txt
    ```
    In questo caso, `2>` indica che tutti i messaggi di errore devono essere inviati al file `error.txt`.

4. **Verifica del file di errore**:
    ```shell
    sysadmin@localhost:~$ cat error.txt
    ls: cannot access /fake: No such file or directory
    ```
    Utilizzando `cat error.txt`, puoi confermare che i messaggi di errore sono stati inviati correttamente al file `error.txt`.

Vediamo come redirigere sia **STDOUT** che **STDERR**:
### Esempio con `ls`:
1. **Comando che produce sia STDOUT che STDERR**:
    ```shell
    sysadmin@localhost:~$ ls /fake /etc/ppp
    ls: cannot access /fake: No such file or directory
    /etc/ppp:
    ip-down.d  ip-up.d
    ```

2. **Redirezione solo di STDOUT**:
    ```shell
    sysadmin@localhost:~$ ls /fake /etc/ppp > example.txt
    ls: cannot access /fake: No such file or directory
    sysadmin@localhost:~$ cat example.txt
    /etc/ppp:
    ip-down.d
    ip-up.d
    ```
    In questo caso, STDOUT è inviato a `example.txt`, mentre STDERR è ancora visualizzato sul terminale.

3. **Redirezione solo di STDERR**:
    ```shell
    sysadmin@localhost:~$ ls /fake /etc/ppp 2> error.txt
    /etc/ppp:
    ip-down.d
    ip-up.d
    sysadmin@localhost:~$ cat error.txt
    ls: cannot access /fake: No such file or directory
    ```
    Qui, STDERR è inviato a `error.txt`, mentre STDOUT è ancora visualizzato sul terminale.

4. **Redirezione di entrambi STDOUT e STDERR nello stesso file**:
    ```shell
    sysadmin@localhost:~$ ls /fake /etc/ppp &> all.txt
    sysadmin@localhost:~$ cat all.txt
    ls: cannot access /fake: No such file or directory
    /etc/ppp:
    ip-down.d
    ip-up.d
    ```
    Con `&>`, sia STDOUT che STDERR sono inviati a `all.txt`.

5. **Redirezione di STDOUT e STDERR in file separati**:
    ```shell
    sysadmin@localhost:~$ ls /fake /etc/ppp > example.txt 2> error.txt
    sysadmin@localhost:~$ cat error.txt
    ls: cannot access /fake: No such file or directory
    sysadmin@localhost:~$ cat example.txt
    /etc/ppp:
    ip-down.d
    ip-up.d
    ```

Comprendere la redirezione di **STDIN** può essere complicato, poiché è più difficile capire perché si dovrebbe voler redirezionare STDIN rispetto a STDOUT e STDERR. Vediamo alcuni concetti chiave e un esempio pratico per chiarire questa funzionalità.

### Redirezione di STDIN
- **STDIN** (Standard Input) è l'input fornito dall'utente tramite la tastiera.
- La maggior parte dei comandi accetta nomi di file come argomenti, ma alcuni comandi possono leggere i dati direttamente da STDIN se non viene specificato un nome di file.

### Esempio con il comando `cat`
1. **Usare `cat` senza argomenti**:
    ```shell
    sysadmin@localhost:~$ cat
    hello
    hello
    how are you?
    how are you?
    goodbye
    goodbye
    ```
    Se non viene fornito un nome di file come argomento, `cat` legge i dati da STDIN. Il comando `cat` visualizza ciò che l'utente digita.

2. **Redirezionare l'output di `cat` a un file**:
    ```shell
    sysadmin@localhost:~$ cat > new.txt
    Hello
    How are you?
    Goodbye
    sysadmin@localhost:~$ cat new.txt
    Hello
    How are you?
    Goodbye
    ```
    In questo esempio, l'output di `cat` viene rediretto al file `new.txt`. Questo può essere utile per aggiungere testo a un file esistente o creare un nuovo file.

### Usare `tr` per la traduzione dei caratteri
1. **Comando `tr` senza supporto per argomenti di nome file**:
    ```shell
    sysadmin@localhost:~$ tr 'a-z' 'A-Z'
    watch how this works
    WATCH HOW THIS WORKS
    ```
    `tr` prende STDIN dalla tastiera e converte tutte le lettere minuscole in maiuscole, inviando STDOUT al terminale.

2. **Redirezionare STDIN da un file**:
    ```shell
    sysadmin@localhost:~$ tr 'a-z' 'A-Z' < example.txt
    /ETC/PPP:
    IP-DOWN.D
    IP-UP.D
    ```
    Utilizzando il carattere `<`, il comando `tr` legge i dati da `example.txt` invece che dalla tastiera.

3. **Redirezionare l'output di `tr` a un altro file**:
    ```shell
    sysadmin@localhost:~$ tr 'a-z' 'A-Z' < example.txt > newexample.txt
    sysadmin@localhost:~$ cat newexample.txt
    /ETC/PPP:
    IP-DOWN.D
    IP-UP.D
    ```
    In questo modo, l'output tradotto viene salvato nel file `newexample.txt`.



### **Comando `grep`**
Il comando `grep` può essere utilizzato per filtrare le righe in un file o l'output di un altro comando che corrispondono a un pattern specificato. Il pattern può essere un testo semplice o può utilizzare espressioni regolari.

1. **Trovare utenti con shell BASH**:
    ```shell
    sysadmin@localhost:~$ grep bash /etc/passwd
    root:x:0:0:root:/root:/bin/bash
    sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash
    ```

2. **Evidenziare i match con `--color`**:
    ```shell
    sysadmin@localhost:~$ grep --color bash /etc/passwd
    ```

3. **Contare le righe che corrispondono al pattern con `-c`**:
    ```shell
    sysadmin@localhost:~$ grep -c bash /etc/passwd
    2
    ```

4. **Mostrare i numeri di riga originali con `-n`**:
    ```shell
    sysadmin@localhost:~$ grep -n bash /etc/passwd
    1:root:x:0:0:root:/root:/bin/bash
    27:sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash
    ```

5. **Invertire il match con `-v`**:
    ```shell
    sysadmin@localhost:~$ grep -v nologin /etc/passwd
    ```

6. **Ignorare maiuscole e minuscole con `-i`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep -i the newhome.txt
    ```

7. **Cercare solo parole intere con `-w`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep -w are newhome.txt
    ```

### **Nota**
Sulle macchine virtuali, il comando `grep` è configurato per includere automaticamente l'opzione `--color`.


### **Carattere punto (.)**
- Il punto (`.`) corrisponde a qualsiasi carattere tranne il carattere di nuova riga.
- È molto utile per trovare pattern flessibili all'interno di testi.

1. **Contenuto del file `red.txt`**:
    ```shell
    sysadmin@localhost:~/Documents$ cat red.txt
    red
    reef
    rot
    reeed
    rd
    rod
    roof
    reed
    root
    reel
    read
    ```

2. **Trovare linee con `r..f`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 'r..f' red.txt
    reef
    roof
    ```
    Il pattern `r..f` trova qualsiasi riga che contiene una `r` seguita esattamente da due caratteri qualsiasi e poi una `f`.

3. **Trovare pattern nel file `/etc/passwd`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 'r..t' /etc/passwd
    root:x:0:0:root:/root:/bin/bash
    operator:x:1000:37::/root:
    ```
    Anche in questo caso, il pattern `r..t` trova righe che contengono `r` seguita da due caratteri e poi `t`.

4. **Trovare parole con almeno quattro caratteri**:
    ```shell
    sysadmin@localhost:~/Documents$ grep '....' red.txt
    reef
    reeed
    roof
    reed
    root
    reel
    read
    ```
    Il pattern `....` trova parole con almeno quattro caratteri.


### **Parentesi quadre `[ ]`**
Le parentesi quadre consentono di specificare un singolo carattere da un elenco o un intervallo di caratteri possibili contenuti all'interno delle parentesi.

1. **Contenuto del file `profile.txt`**:
    ```shell
    sysadmin@localhost:~/Documents$ cat profile.txt
    Hello my name is Joe.
    I am 37 years old.
    3121991
    My favorite food is avocados.
    I have 2 dogs.
    123456789101112
    ```

2. **Trovare righe con numeri utilizzando `[0-9]`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep '[0-9]' profile.txt
    I am 37 years old.
    3121991
    I have 2 dogs.
    123456789101112
    ```
    Il pattern `[0-9]` trova tutte le righe che contengono almeno un numero.

3. **Specificare un intervallo di caratteri**:
    ```shell
    sysadmin@localhost:~/Documents$ grep '[a-d]' profile.txt
    ```
    Le parentesi possono contenere caratteri elencati individualmente `[abcd]` o intervalli `[a-d]`.

4. **Utilizzare il simbolo `^` per negare i caratteri**:
    ```shell
    sysadmin@localhost:~/Documents$ grep '[^0-9]' profile.txt
    Hello my name is Joe.
    I am 37 years old.
    My favorite food is avocados.
    I have 2 dogs.
    ```
    Inserendo `^` come primo carattere all'interno delle parentesi, il pattern trova righe che non contengono i caratteri specificati.


### **Asterisco `*`**
L'asterisco (`*`) è usato per indicare zero o più occorrenze del carattere che lo precede.

### **Parentesi quadre `[ ]`**
Le parentesi quadre consentono di specificare una lista o un intervallo di caratteri da abbinare.


1. **Contenuto del file `red.txt`**:
    ```shell
    sysadmin@localhost:~/Documents$ cat red.txt
    red
    reef
    rot
    reeed
    rd
    rod
    roof
    reed
    root
    reel
    read
    ```

2. **Utilizzo del pattern `re*d`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 're*d' red.txt
    red
    reeed
    rd
    reed
    ```
    Il pattern `re*d` trova qualsiasi riga che contiene `r` seguito da zero o più `e`, e poi `d`.

3. **Utilizzo delle parentesi quadre `[oe]*`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 'r[oe]*d' red.txt
    red
    reeed
    rd
    rod
    reed
    ```
    Il pattern `[oe]*` trova zero o più occorrenze dei caratteri `o` o `e`.

4. **Esempi di pattern che abbinano qualsiasi riga**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 'z*' red.txt
    sysadmin@localhost:~/Documents$ grep 'e*' red.txt
    ```
    Questi pattern non sono molto utili perché l'asterisco abbinerebbe anche zero occorrenze, trovando quindi ogni riga.

5. **Refinire il pattern con `ee*`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 'ee*' red.txt
    reef
    reeed
    reed
    reel
    read
    ```
    Il pattern `ee*` trova righe che contengono almeno una `e`, seguita da zero o più `e`.


### **Caratteri di ancoraggio**
I caratteri di ancoraggio sono usati per specificare se un pattern deve apparire all'inizio o alla fine della linea.

1. **Contenuto del file `/etc/passwd`**:
    ```shell
    sysadmin@localhost:~/Documents$ grep 'root' /etc/passwd
    root:x:0:0:root:/root:/bin/bash
    operator:x:1000:37::/root:
    ```

2. **Carattere di ancoraggio `^` (inizio linea)**:
    ```shell
    sysadmin@localhost:~/Documents$ grep '^root' /etc/passwd
    root:x:0:0:root:/root:/bin/bash
    ```
    Il carattere `^` è utilizzato per assicurarsi che un pattern appaia all'inizio della linea.

3. **Carattere di ancoraggio `$` (fine linea)**:
    ```shell
    sysadmin@localhost:~/Documents$ cat alpha-first.txt
    A is for Animal
    B is for Bear
    C is for Cat
    D is for Dog
    E is for Elephant
    F is for Flower

    sysadmin@localhost:~/Documents$ grep 'r$' alpha-first.txt
    B is for Bear
    F is for Flower
    ```
Il pattern `r$` trova solo le righe che terminano con la lettera `r`, escludendo le altre.

### Comportamento di `grep 're*'`

Il comando cerca la lettera `r` seguita da zero o più `e`, quindi trova ogni riga contenente `r`.

```bash
sysadmin@localhost:~/Documents$ grep 're*' newhome.txt
Thanks for purchasing your new home!!
**Warning** it may be haunted.
There are three bathrooms.
**Beware** of the ghost in the bedroom.
The kitchen is open for entertaining.
**Caution** the spirits don't like guests.
```

### Cercare il carattere `*` letterale

Per cercare la stringa `re*`, bisogna usare il backslash `\*`:

```bash
sysadmin@localhost:~/Documents$ grep 're\*' newhome.txt
**Beware** of the ghost in the bedroom.
```

Così `grep` non interpreta `*` come un quantificatore ma come un carattere normale.



## Extended regular expression

Nel caso delle espressioni regolari estese, l'uso dell'opzione `-E` con `grep` consente di riconoscere simboli come `?`, `+`, e `|` senza bisogno di un comando separato come `egrep`.

### Dettaglio dei simboli estesi:

- **`?`**: Corrisponde al carattere precedente zero o una volta (opzionale).
- **`+`**: Corrisponde al carattere precedente una o più volte.
- **`|`**: Funziona come un "or" logico, corrispondendo a una delle due opzioni.

### Esempi:

1. **Cercare "colo" seguito da una "u" opzionale, e poi "r"**:
    
  ```
   sysadmin@localhost:~/Documents$ grep -E 'colou?r' spelling.txt    
   American English: Do you consider gray to be a color or a shade?
British English: Do you consider grey to be a colour or a shade 
```
    
3. **Cercare una o più "e" in sequenza**:
	``` 
    sysadmin@localhost:~/Documents$ grep -E 'e+' red.txt
    
    red
    reef
    reeed
    reed
    reel
    read

	```
4. **Cercare "gray" o "grey"**:

    ```bash
    sysadmin@localhost:~/Documents$ grep -E 'gray|grey' spelling.txt
    ```

    ```
    American English: Do you consider gray to be a color or a shade?
    British English: Do you consider grey to be a colour or a shade?
    ```


In generale, l'opzione `-E` permette di usare queste espressioni regolari avanzate direttamente con `grep`, senza bisogno di `egrep`.