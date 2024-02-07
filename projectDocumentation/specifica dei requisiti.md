
![logo](../resources/logo/img/logo_small.png)  

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;*Progetto: VetiverJava*  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;*Organizzazione: Yoshimura*  
# Documento di Specifica dei Requisiti del Software VetiverJava

*Versione 1.0*  
*Data: Gennaio 2023*  


***
<ul>

>[!NOTE]  
>All'interno del presente documento sono presenti hyperlink di rimando verso sezioni interne al medesimo documento, altra documentazione di progetto, o risorse esterne.    
>Per una lettura più agevole, se ne consiglia dunque la visione tramite Github o un editor di testo compatibile con [GFM](https://github.github.com/gfm/#what-is-github-flavored-markdown-).  

</ul>  

***  

- Salta all'[Indice](#4-indice)  

## 1 Introduzione

<ul>


### 1.1 Scopo del Documento 
Questo documento viene redatto con la finalità di specificare i requisiti funzionali, non funzionali e di dominio aggiornati per il sistema software "VetiverJava".  
Il documento segue le indicazioni contenute nello standard “IEEE Recommended Practice for Software Requirements Specifications”, avente riferimento IEEE Std 830-1998.  

### 1.2 Scopo del Prodotto  
Il software è progettato per migliorare la gestione delle operazioni quotidiane di una profumeria, migliorando l'efficienza e la precisione delle attività svolte.  
Particolare interesse è rivolto a massimizzare la percentuale di vendite concluse con successo,  
attraverso uno strumento che orienti l’utilizzatore a proporre al cliente prodotti in modo più mirato e il più possibile in linea con le preferenze espresse.  

### 1.3 Glossario  
Si rimanda al [documento](./glossario.md) apposito.

### 1.4 Riferimenti
IEEE Recommended Practice for Software Requirements Specifications, [IEEE Std 830-1998](https://www.cse.msu.edu/~cse870/IEEEXplore-SRS-template.pdf).   
<!-- link alternativi 
http://www.math.uaa.alaska.edu/~afkjm/cs401/IEEE830.pdf  
https://personal.utdallas.edu/~chung/RE/IEEE830-1993.pdf  
https://docs.google.com/file/d/0B0J1w54VjlTjMzJjZTg5M2EtYTdlZC00NjI2LTk0NWMtMzNlNjQxNmQ3NTRi/edit?resourcekey=0-DkFQVGa3pZCD2syV8xzc4w  
-->

</ul>

## 2. Descrizione Generale

<ul>

### 2.1 Prospettiva del Prodotto
Il prodotto software VetiverJava è un sistema autonomo ed è finalizzato ad essere integrato nell'ambiente operativo della profumeria.  
Il software sarà utilizzato dai dipendenti della profumeria per gestire l'inventario, le vendite, i clienti e altre attività correlate alla gestione del punto vendita.  

### 2.2 Funzionalità del Prodotto
Il sistema di gestione della profumeria dovrà fornire le seguenti funzionalità principali:

<ul>

#### 2.2.1 Gestione dei Clienti
<a name="gestione-clienti"> </a>
Registrazione e gestione dei dati dei clienti, inclusi nominativo, tessera e storico degli acquisti.  

#### 2.2.2 Gestione delle Vendite
<a name="gestione-vendite"> </a>
Registrazione delle transazioni di vendita, includendo dettagli come prodotti acquistati, quantità, prezzo e dati del cliente (se tesserato).  

#### 2.2.3 Gestione dell'Inventario
Aggiunta, modifica e rimozione di articoli dall'inventario.  
È previsto che il sistema tenga traccia del livello di stock corrente di ciascun prodotto,   
aggiorni automaticamente l’inventario dopo ogni vendita.  
e generi avvisi quando il livello di stock di un articolo raggiunge una soglia critica.  

#### 2.2.4 Ricerca Base
<a name="ricerca-base">  </a>
Ricerca e visualizzazione delle disponibilità a inventario per brand (disponibilità di tutte le referenze del marchio)  
oppure per nome della fragranza (disponibilità dello specifico articolo).

#### 2.2.5 Ricerche Avanzate  
<a name="ricerche-avanzate">  </a> 
Ricerca e visualizzazione delle disponibilità a inventario di fragranze che possiedono determinate [note olfattive](./glossario.md#note-olfattive)  
o che appartengono a una [famiglia olfattiva](./glossario.md#famiglie-olfattive) specifica.  
Queste funzionalità presuppongono gestioni automatiche della classificazione  
e algoritmi di ordinamento che producano la miglior affinità rispetto ai criteri di ricerca.

#### 2.2.6 Gestione Tester
Memorizzazione della quantità di bottiglie [tester](./glossario.md#tester) disponibili per ogni fragranza  
e aggiornamento automatico della quantità stimata di prodotto nel [tester](./glossario.md#tester) di corrente utilizzo dopo ogni test effettuato col cliente,  
con possibilità di correzione manuale.  

#### 2.2.7 Gestione Decant
Aggiornamento automatico delle quantità residue di prodotto contenuto nelle boccette dedicate ai [decant](./glossario.md#decant) dopo ogni prelievo e guida all'apertura di nuove boccette secondo criteri definiti.  
È previsto che il sistema tenga traccia delle quantià dei materiali di consumo e che notifichi l'utente quando le rimanenze scendono sotto a una soglia critica.  


</ul>

### 2.3 Caratteristiche Utente
Il sistema software VetiverJava è utilizzato dal personale della profumeria, al quale è richiesta una basilare conoscenza del dominio.

</ul>


## 3. Requisiti Specifici
<ul>

### 3.1 Requisiti Funzionali
- **RF1: Login**    
	- Il sistema dovrà consentire le operazioni di log-in e log-out, attraverso credenziali univoche per ogni [utente](./glossario.md#utente).  
- **RF2: Registrazione Scheda Cliente**    
	- Il sistema dovrà permettere all'[utente](./glossario.md#utente) il tesseramento di nuovi clienti attraverso l'inserimento di Nome e Cognome, e assegnare automaticamente un numero di tessera in maniera incrementale.
- **RF3: Cronologia Acquisti**    
	- Il sistema dovrà tenere traccia degli acquisti dei clienti tesserati  
	e rendere disponibili le informazioni all'[utente](./glossario.md#utente) attraverso una ricerca dedicata, tramite nome e cognome oppure numero di tessera.
- **RF4: Report Vendite**    
	- Il sistema dovrà memorizzare qualsiasi transazione di vendita,  
	e generare un report giornaliero abbinato all’[utente](./glossario.md#utente) loggato.  
- **RF5: Gestione Fragranze**    
	- **RF5.1:**    
	Il sistema dovrà permettere l’inserimento in archivio di nuove fragranze disponibili a magazzino,  
	e la rimozione di fragranze già presenti per dismissione del marchio o qualsivoglia altro motivo.  
	- **RF5.2:**    
	Il sistema dovrà aggiornare automaticamente le disponibilità dopo ogni vendita effettuata.  
	- **RF5.3:**    
	Il sistema dovrà permettere all'[utente](./glossario.md#utente) l'aggiornamento manuale delle disponibilità per i nuovi rifornimenti.  
	- **RF5.4:**    
	Il sistema dovrà notificare l'[utente](./glossario.md#utente) quando la disponibilità di un articolo scende sotto una soglia critica (da stabilire).  
- **RF6: Ricerca Base**    
	- Il sistema dovrà permettere la ricerca e visualizzazione delle disponibilità a inventario per brand (disponibilità di tutte le referenze del marchio) oppure per nome della fragranza (disponibilità dello specifico articolo).
- **RF7: Gestione Note Olfattive**    
	- **RF7.1:**    
	Il sistema dovrà memorizzare una lista di [note olfattive](./glossario.md#note-olfattive) conosciute e i relativi contributi di appartenenza alle [famiglie olfattive](./glossario.md#famiglie-olfattive).  
	- **RF7.2:**    
	L’[utente](./glossario.md#utente) dovrà poter procedere all’inserimento di nuove [note olfattive](./glossario.md#note-olfattive) in elenco,  
	attraverso un'interfaccia che gli permetta di selezionarne i relativi contributi.  
	- **RF7.3:**    
	Il sistema dovrà rendere possibile la ricerca tra le [note](./glossario.md#note-olfattive) già presenti in elenco e la modifica dei dettagli relativi:  
	in particolare, all'[utente](./glossario.md#utente) non dovrà essere consentita l'eliminazione di una [nota](./glossario.md#note-olfattive) dall'elenco, ma soltanto l'eventuale modifica dei contributi di appartenenza alle [famiglie olfattive](./glossario.md#famiglie-olfattive).  
- **RF8: Appartenenza alle Famiglie Olfattive**    
	- Il sistema dovrà determinare automaticamente il grado di appartenenza ad ogni [famiglia olfattiva](./glossario.md#famiglie-olfattive) di ciascuna fragranza a inventario, basandosi sulle [note](./glossario.md#note-olfattive) presenti in [piramide](./glossario.md#piramide-olfattiva).  
- **RF9: Ricerca Avanzata per Note Olfattive**    
	- **RF9.1:**    
	Il sistema dovrà permettere la ricerca a inventario delle fragranze che contengano una o più [note olfattive](./glossario.md#note-olfattive) specifiche,  
	fornendo la possibilità di escludere dai risultati quelle contenenti altre [note](./glossario.md#note-olfattive) specifiche.  
	Come risultato della ricerca,  
	il sistema dovrà mostrare a video una lista di 3 fragranze tra quelle disponibili,  
	disposte in ordine di maggiore affinità con la ricerca, secondo i criteri illustrati in [RD8](#rd8).  
	- **RF9.2:**    
	La schermata dovrà altresì consentire la ripetizione del processo,  
	mostrando le successive fragranze in classifica, a gruppi di tre per ogni iterazione.  
- **RF10: Ricerca Avanzata per Famiglia Olfattiva**    
	- **RF10.1:**    
	Il sistema dovrà permettere di effettuare una ricerca attraverso la selezione di una [famiglia olfattiva](./glossario.md#famiglie-olfattive) specifica.  
	Come risultato della ricerca,  
	il sistema dovrà mostrare a video una lista di 3 fragranze tra quelle disponibili,  
	disposte in ordine di maggiore percentuale di appartenenza, secondo il criterio illustrato in [RD7](#rd7).  
	- **RF10.2:**    
	La schermata dovrà altresì consentire la ripetizione del processo,  
	mostrando le successive fragranze in classifica, a gruppi di tre per ogni iterazione.  
- **RF11: Gestione Tester**    
	- **RF11.1:**    
	Il sistema dovrà tenere traccia della quantità di bottiglie [tester](./glossario.md#tester) disponibili per ogni fragranza, i relativi [formati](./glossario.md#formati), e la quantità di prodotto contenuta nel tester di corrente utilizzo.  
	- **RF11.2:**    
	L'interfaccia dovrà permettere di selezionare quali tra i risultati proposti dalle funzionalità di [Ricerca Avanzata](#ricerche-avanzate) saranno effettivamente oggetto di test col cliente,  
	e aggiornare automaticamente la quantità stimata di prodotto nel [tester](./glossario.md#tester) di corrente utilizzo dopo ogni test effettuato col cliente, secondo quanto esposto in [RD9.2](#rd9.2).    
	- **RF11.3:**    
	Vista l’alta variabilità data dagli [atomizzatori](./glossario.md#atomizzatori) differenti dei diversi prodotti,  
	e la conseguente impossibilità di effettuare un calcolo preciso dei consumi,  
	il sistema dovrà fornire all’[utente](./glossario.md#utente) la possibilità di intervenire manualmente e modificare la quantità rimanente nel [tester](./glossario.md#tester) corrente, qualora venissero riscontrate differenze rilevanti tra la stima effettuata dal sistema e la situazione reale.  	
- **RF12: Gestione Decant**    
	- **RF12.1:**     
	L’interfaccia dovrà permettere di selezionare quali tra i risultati proposti dalle funzionalità di ricerca saranno oggetto di [decant](./glossario.md#decant).  
	- **RF12.2:**  
	Il sistema dovrà suggerire a video il formato corretto per una eventuale apertura di una boccetta nuova,  
nel rispetto dei criteri indicati in [RD10.2](#rd10.2).  
	- **RF12.3:**    
	Il sistema dovrà aggiornare automaticamente le disponibilità residue nelle boccette dedicate dopo ogni prelievo.  
	- **RF12.4:**    
	Il sistema dovrà fornire all’[utente](./glossario.md#utente) la possibilità di registrare le quantità di fiale e materiali di consumo appositi disponibili a magazzino,  
	aggiornare automaticamente le rimanenze dopo ogni vendita,  
	e notificare a video quando queste scendono sotto alle 10 unità.  
	

### 3.2 Requisiti Non Funzionali 
- **RNF1: Piattaforma di Esecuzione**   
	- Il sistema VetiverJava dovrà essere progettato per essere eseguito su qualsiasi dispositivo munito di Java Virtual Machine (JVM), versione compatibile con Java 8 o successiva.  
	Questo requisito mira a garantire la portabilità del software, consentendo l'esecuzione su una vasta gamma di 	dispositivi hardware.  
- **RNF2: Linguaggio di Programmazione**    
	- Il software VetiverJava dovrà essere implementato utilizzando il linguaggio di programmazione Java versione 8.  
	Questa scelta è essenziale per garantire coerenza nella base tecnologica e facilitare la manutenzione del sistema.  
- **RNF3: Prestazioni**    
	- È richiesta rapidità nell’esecuzione delle funzioni:  
	l’[utente](./glossario.md#utente) può attendere al massimo 5 secondi per visualizzare a video i risultati delle [ricerche avanzate](#ricerche-avanzate),  
	mentre i tempi per le operazioni di [gestione del cliente](#gestione-clienti) e [registrazione delle vendite](#gestione-vendite) non devono superare i 3 secondi. 
- **RNF4: Usabilità**    
	- L’interfaccia dovrà essere snella e intuitiva,  
	e guidare l’[utente](./glossario.md#utente) nelle azioni, attraverso bottoni o poche scelte di immediata comprensione.  
	Piuttosto che avere molte funzionalità concentrate in un’unica schermata sovraccarica di informazioni,  
	si prediligono schermate diverse, dedicate a poche operazioni concettualmente affini.  
- **RNF5: Tempo di apprendimento**    
	- Il tempo medio di apprendimento per l’uso della piattaforma dovrà essere inferiore alle 2 ore.  
	L'obiettivo è limitare al minimo l’interruzione delle normali attività lavorative, riducendo il time-to-proficiency per gli utenti.  
- **RNF6: Lingua dell’interfaccia Utente**    
	- L'interfaccia utente del programma dovrà essere completamente in lingua inglese.  
	Questa scelta è finalizzata a garantire una standardizzazione nella comunicazione dei termini tipici del dominio e nell'utilizzo del software da parte degli [utenti](./glossario.md#utente).  
- **RNF7: Lingua della Documentazione**    
	- La documentazione finale fornita a corredo del software dovrà essere in doppia versione, italiana e inglese.    
- **RNF8: Consegna**    
	- La piattaforma dovrà essere operativa a partire da Aprile 2024.  


### 3.3 Requisiti di Dominio
- **RD1: Acquisto**    
	- L’acquisto in negozio è permesso sia a clienti tesserati,  
	che a clienti non tesserati (e che non si vogliono tesserare). 
- **RD2: Identificativo fragranza**  
	- Ogni profumo a inventario è identificato univocamente dalla combinazione di brand di appartenenza, nome della fragranza e [concentrazione](./glossario.md#concentrazione).  
	Profumi con brand e nome uguali, ma [concentrazioni](./glossario.md#concentrazione) differenti, NON sono lo stesso profumo.
- **RD3: Dati fragranza**    
	- L’inserimento di una nuova fragranza in archivio prevede la memorizzazione del brand di appartenenza, il nome della fragranza, la [concentrazione](./glossario.md#concentrazione), la [piramide olfattiva](./glossario.md#piramide-olfattiva), i [formati](./glossario.md#formati), le disponibilità e i prezzi relativi.  
- **RD4: Piramide Olfattiva**    
	- La memorizzazione della [piramide](./glossario.md#piramide-olfattiva) di una fragranza può avvenire soltanto attraverso l’utilizzo di [note](./glossario.md#note-olfattive) già censite,  
	quindi, contestualmente all’aggiunta a inventario di una fragranza,  
	nel caso questa avesse delle [note](./glossario.md#note-olfattive) non presenti in archivio,  
	il sistema dovrà richiedere l’inserimento in elenco delle [note](./glossario.md#note-olfattive) sconosciute, con i relativi contributi per le [famiglie olfattive](./glossario.md#famiglie-olfattive).  
- **RD5: Note Olfattive**    
	- Ciascuna [nota olfattiva](./glossario.md#note-olfattive) è caratterizzata da un contributo di appartenenza ad ogni [famiglia olfattiva](./glossario.md#famiglie-olfattive),  
	identificato da un valore numerico da 0 a 5.
- **RD6: Famiglie Olfattive**  
	- Il committente richiede che nel progetto non si faccia riferimento alle 7 [famiglie olfattive](./glossario.md#famiglie-olfattive) ufficiali riconosciute dalla Société Française des Parfumeurs,  
	bensì alle più numerose [sfaccettature olfattive](./glossario.md#sfaccettature-olfattive) elencate dall’Accademia del Profumo.
- **RD7: Grado di appartenenza alle Famiglie Olfattive**    
<a name="RD7">  </a>  
	- Il grado di appartenenza di una fragranza ad una specifica [famiglia olfattiva](./glossario.md#famiglie-olfattive) è espresso da un coefficiente percentuale,  
	proporzionale al rapporto tra la somma dei singoli contributi di ciascuna [nota](./glossario.md#note-olfattive) presente in [piramide](./glossario.md#piramide-olfattiva) e relativi alla [famiglia](./glossario.md#famiglie-olfattive) in questione, e la somma dei contributi massimi possibili per quella quantità di [note](./glossario.md#note-olfattive).  
- **RD8: Criterio di ordinamento per la Ricerca Avanzata per Note Olfattive**    
<a name="RD8">  </a>  
	- La presenza delle [note](./glossario.md#note-olfattive) selezionate dovrà avere un peso differente in base alla posizione tra i [piani olfattivi](./glossario.md#piani-olfattivi) della [piramide](./glossario.md#piramide-olfattiva) della fragranza [^1].  
	Questo peso segue un ordine decrescente, che attribuisce maggiore importanza alle [note di fondo](./glossario.md#note-di-fondo) rispetto alle [note di cuore](./glossario.md#note-di-cuore) e a quelle di [testa](./glossario.md#note-di-testa).  
	L’eventuale ripetizione delle [note](./glossario.md#note-olfattive) selezionate su più [piani olfattivi](./glossario.md#piani-olfattivi) conferisce un peso extra.  
	In particolar modo,  
	per illustrare il criterio di ordinamento con un'analogia numerica,  
	la presenza di una [nota](./glossario.md#note-olfattive) selezionata nel [piano olfattivo](./glossario.md#piani-olfattivi) di [testa](./glossario.md#note-di-testa) è valutata con peso 1,  
	nel [piano olfattivo](./glossario.md#piani-olfattivi) di [cuore](./glossario.md#note-di-cuore) con peso 2,  
	tra le [note di fondo](./glossario.md#note-di-fondo) con peso 3,  
	e la ripetizione su più [piani](./glossario.md#piani-olfattivi) aggiunge ulteriormente un peso di 2.  
- **RD9: Test Fragranze e Tester**    
	- **RD9.1:**    
	I test delle fragranze vengono effettuati prelevando la fragranza esclusivamente da specifiche bottiglie [tester](./glossario.md#tester). 
	- **RD9.2:**    
<a name="RD9.2"> </a> 
	Ogni test è effettuato facendo 5-7 spruzzi su [mouillettes](./glossario.md#mouillettes),  
	che consumano indicativamente 1ml di prodotto.  
	- **RD9.3:**    
	I test sono gratuiti per il cliente, e il loro numero è limitato a discrezione dell'[utente](./glossario.md#utente).  
	- **RD9.4:**    
	Una fragranza a inventario per la quale non è presente disponibilità di [tester](./glossario.md#tester),  
	dovrà essere comunque disponibile per tutte le funzioni di ricerca [base](#ricerca-base) e [avanzate](#ricerche-avanzate), per la vendita, ma non dovrà essere disponibile per il test.  
	- **RD9.5:**  
	Le bottiglie [tester](./glossario.md#tester) sono escluse dalla vendita, anche se nuove e sigillate.  
- **RD10: Decant**  
	- **RD10.1:**   
	I [decant](./glossario.md#decant) hanno un formato predefinito di 5ml e vengono prelevati da boccette standard (NO [tester](./glossario.md#tester)).    
	- **RD10.2:**  
<a name="RD10.2"> </a>
	Per il primo prelievo, viene utilizzata la boccetta nel formato più piccolo tra quelli disponibili per la fragranza oggetto di [decant](./glossario.md#decant).  
	Dopo il primo prelievo, tale boccetta verrà destinata solo al [decantaggio](./glossario.md#decant), e quindi non potrà essere venduta.  
	- **RD10.3:**    
	Si può togliere dalla disponibilità di vendita e dedicare al [decantaggio](./glossario.md#decant) una boccetta nuova soltanto nel caso in cui le unità disponibili a magazzino di tale fragranza siano in numero maggiore di 2.  
	- **RD10.4:**    
	Un [decant](./glossario.md#decant) è venduto al costo di listino/ml, oltre a un costo fisso (da stabilire) per i materiali di consumo e il servizio. 

</ul>

## 4. Indice

1. [Introduzione](#1-introduzione)  
1.1 [Scopo del Documento](#11-scopo-del-documento)  
1.2 [Scopo del Prodotto](#12-scopo-del-prodotto)  
1.3 [Glossario](#13-glossario)  
1.4 [Riferimenti](#14-riferimenti)  
2. [Descrizione Generale](#2-descrizione-generale)  
2.1 [Prospettiva del Prodotto](#21-prospettiva-del-prodotto)  
2.2 [Funzionalità del Prodotto](#22-funzionalità-del-prodotto)   
2.3 [Caratteristiche Utente](#23-caratteristiche-utente)   
3. [Requisiti Specifici](#3-requisiti-specifici)  
3.1 [Requisiti Funzionali](#31-requisiti-funzionali)  
3.2 [Requisiti Non Funzionali](#32-requisiti-non-funzionali)  
3.3 [Requisiti di Dominio](#33-requisiti-di-dominio)  
4. [Indice](#4-indice)  





[^1]:Sebbene per definizione come da [Glossario](./glossario.md) le [note di testa](./glossario.md#note-di-testa) siano quelle che si percepiscono immediatamente dopo aver spruzzato il profumo e che costituiscono la prima impressione olfattiva che si ha di un profumo, seguite da [cuore](./glossario.md#note-di-cuore) e [fondo](./glossario.md#note-di-fondo),  
il criterio di ordinamento deve invece, su espressa richiesta del committente, invertire quest’ordine, prediligendo le [note di fondo](./glossario.md#note-di-fondo), con pesi proporzionali a quanto descritto.  
Infatti,  
nell'ipotesi in cui il cliente manifesti l'interesse per una specifica [nota](./glossario.md#note-olfattive) e gli venga presentato un campione che la manifesta in apertura,   
sussiste il potenziale rischio che il cliente possa essere indotto in errore nell'acquisto di un prodotto che durante l’[evoluzione](./glossario.md#evoluzione) si discosta dalle sue preferenze.  
Al contrario,  
nel caso in cui il cliente mostri apprezzamento per un profumo che,  
pur non presentando necessariamente le caratteristiche richieste già dall’apertura,  
le incorpora gradualmente nel corso della sua [evoluzione](./glossario.md#evoluzione) e nel [drydown](./glossario.md#drydown),  
si può confidare che tale processo risponda in modo più preciso ai gusti specifici espressi.  
Il committente ritiene pertanto che tale approccio determini una maggior soddisfazione della clientela e un incremento degli acquisti conclusi con soddisfazione. 