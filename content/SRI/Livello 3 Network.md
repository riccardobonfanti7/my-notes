# **Il Livello 3 (Network) del modello OSI**

Il **modello OSI (Open Systems Interconnection)** è uno standard concettuale che suddivide la comunicazione di rete in **sette livelli**. Il **Livello 3 (Network)** è fondamentale per il funzionamento di Internet, poiché si occupa della gestione e dell'instradamento dei pacchetti di dati tra reti diverse.  

### **Funzioni principali del Livello 3**
- **Instradamento (Routing):** Determina il percorso migliore per inviare i pacchetti tra mittente e destinatario attraverso la rete. I router operano a questo livello per instradare il traffico.  
- **Indirizzamento IP:** Ogni dispositivo in rete viene identificato da un indirizzo IP univoco, necessario per la comunicazione.  
- **Frammentazione e ricomposizione:** Se un pacchetto è troppo grande per essere trasmesso su una rete specifica, viene suddiviso in unità più piccole e ricomposto alla destinazione.  
- **Gestione della congestione e dell'affidabilità:** Sebbene IP operi in modalità "best effort", alcuni protocolli aggiuntivi (come ICMP) vengono utilizzati per segnalare errori e problemi di rete.  

Il protocollo più importante che opera a livello 3 è **IP (Internet Protocol)**, che è il fondamento della comunicazione su Internet.

## **Caratteristiche del protocollo IP**

1. **Connectionless (senza connessione)**  
   Il protocollo IP è **connectionless**, il che significa che non stabilisce una connessione diretta tra mittente e destinatario prima di inviare i dati. Ogni pacchetto IP viene trasmesso in modo indipendente e può seguire percorsi diversi attraverso la rete. Questo approccio migliora la scalabilità, ma non garantisce che i pacchetti arrivino in ordine o senza perdite.

2. **Media Independent (indipendente dal mezzo trasmissivo)**  
   IP è **media independent**, cioè non dipende dal tipo di rete fisica utilizzata (rame, fibra ottica, Wi-Fi, satellitare, ecc.). Questo perché il protocollo opera a livello di rete (Layer 3 del modello OSI) e può essere trasportato su diverse tecnologie di livello inferiore, come Ethernet, DSL o 5G.

3. **Best Effort (senza garanzia di consegna)**  
   IP utilizza una modalità **best effort**, il che significa che tenta di consegnare i pacchetti nel miglior modo possibile, senza offrire garanzie di successo. Se un pacchetto viene perso o danneggiato, il protocollo IP non lo ritrasmette automaticamente; spetta ai protocolli di livello superiore (come TCP) gestire eventuali errori e ritrasmissioni.

---

## **Motivi del passaggio da IPv4 a IPv6**

L’indirizzamento IPv4 (a 32 bit) permette di generare circa **4,3 miliardi di indirizzi unici**, che con la crescita di dispositivi connessi (PC, smartphone, IoT) sono risultati insufficienti. IPv6, con indirizzi a **128 bit**, offre un numero praticamente illimitato di indirizzi.

### **Altri vantaggi di IPv6**  
- **Eliminazione del NAT**: IPv6 permette a ogni dispositivo di avere un indirizzo pubblico, semplificando la comunicazione diretta.  
- **Maggiore efficienza**: Supporta l’auto-configurazione e una gestione più efficace del traffico di rete.  
- **Migliore sicurezza**: IPv6 integra protocolli di sicurezza come IPsec.  

---

## **Soluzioni adottate per superare i limiti di IPv4**

1. **NAT (Network Address Translation)**  
   Permette a più dispositivi di condividere un unico indirizzo IPv4 pubblico, riducendo il numero di indirizzi necessari.

2. **CIDR (Classless Inter-Domain Routing)**  
   Un sistema di assegnazione degli indirizzi che migliora l’efficienza della subnetting rispetto alle classi IP tradizionali.

3. **DHCP (Dynamic Host Configuration Protocol)**  
   Assegna dinamicamente gli indirizzi IP ai dispositivi, evitando sprechi.

4. **Conservazione degli indirizzi**  
   L’uso più efficiente degli indirizzi disponibili tramite tecniche di subnetting e aggregazione delle route ha permesso di ritardare l’esaurimento di IPv4.

