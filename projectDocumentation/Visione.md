# Documento di Visione


![logo](../resources/logo/img/logo_small.png)



Nel seguente documento viene esposto quanto emerso dai primi colloqui col committente per quanto concerne la definizione dei requisiti per il Sistema Software VetiverJava.  

Il software VetiverJava è progettato per essere integrato all’interno di una profumeria,  
al fine di gestire le operazioni quotidiane, migliorandone l'efficienza e la precisione.  
Il desiderio di questo software nasce soprattutto dall’interesse nell’aumentare la percentuale di vendite concluse con successo,  
attraverso uno strumento che orienti l’utilizzatore a proporre al cliente prodotti in modo più mirato e il più possibile in linea con le preferenze espresse.  

Il sistema è destinato all'utilizzo esclusivo da parte del personale della profumeria,  
da qui in avanti identificato come utente,    
a cui dovrà essere permesso l’accesso tramite registrazione e credenziali univoche.  
Ognuna delle operazioni descritte di seguito nel documento, si intendono effettuate dall’utente,  
unica entità che ha accesso al sistema.  

Deve essere prevista la gestione delle informazioni dei clienti:  
l’utente utilizzatore deve poter registrare una scheda per ogni nuovo cliente,  
identificato da nome, cognome, e numero di tessera assegnato incrementalmente.  
Per ogni cliente registrato deve essere tenuta traccia degli acquisti effettuati.  
L’utente deve poter cercare un cliente nella piattaforma attraverso nome e cognome, oppure numero di tessera, e visualizzarne la cronologia acquisti.  

L’acquisto in negozio è permesso sia a clienti tesserati, 
che a clienti non tesserati (e che non si vogliono tesserare):  
in ogni caso, qualsiasi transazione di vendita deve essere memorizzata dal sistema, 
che dovrà generare un report giornaliero abbinato all’utente loggato.  

Il sistema deve poter memorizzare il catalogo delle fragranze in vendita.  
Ogni profumo a inventario è identificato univocamente con brand di appartenenza, nome della fragranza e concentrazione.   
Si noti che profumi con brand e nome uguali, ma concentrazioni differenti NON sono lo stesso profumo.

L’inserimento di una fragranza a catalogo prevede che oltre a tali dati,  
vengano memorizzati formati, disponibilità e prezzi relativi.  
Per quanto riguarda la gestione dell’inventario,  
il sistema deve permettere l’inserimento in archivio di nuove fragranze disponibili a magazzino,  
l’aggiornamento automatico delle disponibilità dopo ogni vendita effettuata,  
l’aggiornamento manuale delle disponibilità per i nuovi rifornimenti,  
e la rimozione di fragranze già presenti per dismissione del marchio o qualsivoglia altro motivo.  

Il software deve permettere la ricerca e visualizzazione delle disponibilità a inventario per brand (disponibilità di tutte le referenze del marchio)  
oppure per nome della fragranza (disponibilità dello specifico articolo).  
Da qui in avanti, si faccia riferimento a tale funzionalità come *\[Ricerca Base\]*.

Oltre a quelli già citati in precedenza,  
tra i dettagli memorizzati per ciascuna fragranza presente a magazzino,  
deve necessariamente esserci la piramide olfattiva e le relative note olfattive di testa, cuore e fondo.  
È richiesto infatti che il sistema sia in grado di memorizzare un elenco di note olfattive conosciute,  
ciascuna delle quali caratterizzata da un contributo di appartenenza ad ogni famiglia olfattiva,  
identificato da un valore numerico da 0 a 5.  
L’utente deve poter procedere all’inserimento di nuove note olfattive in elenco,  
selezionandone i relativi contributi.  
Deve inoltre poter cercare tra le note già presenti in elenco e modificarne i dettagli relativi:  
in particolare, all’utente non deve essere consentita l’eliminazione di una nota dall’elenco,  
ma soltanto l’eventuale modifica dei contributi di appartenenza alle famiglie olfattive.  
Si noti che la memorizzazione della piramide di una fragranza,  
può avvenire soltanto attraverso l’utilizzo di note già censite,  
quindi, contestualmente all’aggiunta a inventario di una fragranza,  
nel caso questa avesse delle note non presenti in archivio,  
il sistema deve richiedere l’inserimento in elenco delle note sconosciute,  
con i relativi contributi per le famiglie olfattive.  

Basandosi sulle note presenti in piramide,  
il sistema deve inoltre determinare automaticamente, per ciascuna fragranza a inventario, il grado di appartenenza ad ogni famiglia olfattiva [^1] .   
Il grado di appartenenza di una fragranza ad una specifica famiglia olfattiva è espresso da un coefficiente percentuale,  
proporzionale al rapporto tra la somma dei singoli contributi di ciascuna nota presente in piramide e relativi alla famiglia in questione,  
e la somma dei contributi massimi possibili per quella quantità di note.  

Coerentemente con la mission primaria del progetto di fornire uno strumento che guidi l’utilizzatore a proporre in test al cliente prodotti più allineati alle richieste,  
oltre alla *\[Ricerca Base\]* il sistema dovrà offrire delle funzionalità di ricerca avanzate.  
Nello specifico, il sistema dovrà permettere la ricerca a inventario delle fragranze che contengano una o più note olfattive specifiche,  
fornendo la possibilità di escludere dai risultati quelle contenenti altre note specifiche.  
Da qui in avanti, si faccia riferimento a tale funzionalità come *\[Ricerca Avanzata per Note Olfattive\]*.  
La presenza delle note selezionate deve avere un peso differente in base alla posizione tra i piani olfattivi della piramide della fragranza [^2] .  
Questo peso segue un ordine decrescente, che attribuisce maggiore importanza alle note di fondo rispetto alle note di cuore e a quelle di testa.  
L’eventuale ripetizione delle note selezionate su più piani olfattivi conferisce un peso extra.  
In particolar modo,  
per illustrare il criterio di ordinamento con un'analogia numerica,  
la presenza di una nota selezionata nel piano olfattivo di testa è valutata con peso 1,   
nel piano olfattivo di cuore con peso 2,  
tra le note di Fondo con peso 3,  
e la ripetizione su più piani aggiunge ulteriormente un peso di 2.    
Come risultato della ricerca,  
il sistema dovrà mostrare a video una lista di 3 fragranze tra quelle disponibili,   
disposte in ordine di maggiore affinità con la ricerca, secondo i criteri illustrati precedentemente.  
La schermata deve altresì consentire la ripetizione del processo,  
mostrando le successive fragranze in classifica, a gruppi di tre per ogni iterazione.  
Il software deve inoltre permettere di effettuare una ricerca attraverso la selezione di una Famiglia Olfattiva specifica:  
da qui in avanti, si faccia riferimento a tale funzionalità come *\[Ricerca Avanzata per Famiglia Olfattiva\]*.  
Come risultato, il sistema dovrà mostrare a video le fragranze a inventario con più percentuale di appartenenza a quanto selezionato.  
Come già richiesto per la funzionalità di *\[Ricerca Avanzata per Note Olfattive\]*,  
anche in questo caso il sistema dovrà mostrare a video una lista di 3 fragranze tra le disponibili,  
ordinate secondo l’affinità maggiore con la ricerca, con possibilità di reiterazione a gruppi di tre.  

Ognuna delle funzionalità *\[Ricerca Base\]*, *\[Ricerca Avanzata per Note Olfattive\]*, *\[Ricerca Avanzata per Famiglia Olfattiva\]*,  
ha l’obbiettivo di sottoporre in test al cliente alcuni tra i risultati ottenuti:  
l’interfaccia deve quindi permettere di selezionare quali tra i risultati proposti saranno effettivamente oggetto di test.  
I test vengono effettuati prelevando la fragranza esclusivamente da specifiche bottiglie tester,  
facendo 5-7 spruzzi su mouillettes,  
che consumano indicativamente 1ml di prodotto.  
Il sistema deve tenere traccia della quantità di bottiglie tester disponibili per ogni fragranza,  
e aggiornare automaticamente la quantità stimata di prodotto nel tester di corrente utilizzo dopo ogni test effettuato col cliente.  
Vista l’alta variabilità data dagli atomizzatori differenti dei diversi prodotti,  
e la conseguente impossibilità di effettuare un calcolo preciso dei consumi,  
il sistema deve fornire all’utente la possibilità di intervenire manualmente e modificare la quantità rimanente nel tester corrente, qualora venissero riscontrate differenze rilevanti tra la stima effettuata dal sistema e la situazione reale.  
Si tenga presente che una fragranza a inventario per la quale non è presente disponibilità di tester,  
deve essere comunque disponibile per tutte le funzioni di ricerca base e avanzate, per la vendita,  
ma non deve essere disponibile per il test.  
Le bottiglie tester sono invece escluse dalla vendita, anche se nuove e sigillate.  
I test sono gratuiti per il cliente, e il loro numero è limitato a discrezione dell'utente:  
la richiesta di funzionalità di ricerca avanzate mira appunto a test meno dispersivi,  
e al conseguente aumento delle vendite effettive.  


Per fornire ulteriore consapevolezza nella scelta,  
viene fornita al cliente la possibilità di acquistare un decant da 5ml della fragranza individuata,  
per avere modo di testarla più volte in momenti diversi prima dell’acquisto di una full-size.  
Il decant viene prelevato da una boccetta standard (NO Tester),  
e venduto al costo di listino/ml, oltre a un costo fisso (da stabilire) per i materiali di consumo e il servizio.  
Per il primo prelievo, viene utilizzata la boccetta nel formato più piccolo tra quelli disponibili per la fragranza oggetto di decant.  
Dopo il primo prelievo, tale boccetta verrà destinata solo al decantaggio, e quindi non potrà essere venduta.  
Si tenga presente che si può togliere dalla disponibilità di vendita e dedicare al decantaggio una boccetta nuova soltanto nel caso in cui le unità disponibili a magazzino di tale fragranza siano in numero maggiore di 2.  
Analogamente a quanto esposto per i test,  
l’interfaccia deve permettere di selezionare quali tra i risultati proposti dalle funzionalità di ricerca saranno oggetto di decant.  
Il sistema deve quindi tenere traccia delle transazioni di vendita dei decant,  
aggiornare automaticamente le disponibilità residue nelle boccette dedicate,  
e suggerire a video il formato corretto per una eventuale apertura di una boccetta nuova,  
nel rispetto dei criteri sopraindicati.  
Dovrà inoltre fornire all’utente la possibilità di registrare le quantità di fiale e materiali di consumo appositi disponibili a magazzino,
aggiornare automaticamente le rimanenze dopo ogni vendita,  
e notificare a video quando queste scendono sotto alle 10 unità.  

Il sistema verrà eseguito sul pc windows attualmente presente al banco della profumeria,  
ma dovrà essere compatibile con eventuali futuri upgrade della strumentazione hardware.  
Per garantire una standardizzazione nella comunicazione dei termini tipici del dominio e nell'utilizzo del software da parte degli utenti, l’interfaccia dovrà essere completamente in lingua inglese.  
La documentazione finale fornita a corredo del software dovrà invece essere in doppia versione, italiana e inglese.  
L’interfaccia dovrà essere snella e intuitiva,  
e guidare l’utente nelle azioni, attraverso bottoni o poche scelte di immediata comprensione.  
Piuttosto che avere molte funzionalità concentrate in un’unica schermata sovraccarica di informazioni,  
si prediligono schermate diverse, dedicate a poche operazioni concettualmente affini.  
Il tempo di apprendimento per l’uso della piattaforma deve necessariamente essere inferiore alle 2 ore,  
in modo da limitare al minimo l’interruzione delle normali attività lavorative.  
È richiesta rapidità nell’esecuzione delle funzioni:  
l’utente può attendere al massimo 5 secondi per visualizzare a video i risultati delle ricerche avanzate,  
mentre i tempi per le operazioni di gestione del cliente e registrazione delle vendite non devono superare i 3 secondi.  
Si richiede che la piattaforma sia operativa a partire da aprile 2024.  





[^1]:Per non rendere troppo limitante la classificazione,  
il committente richiede che non si faccia riferimento alle 7 famiglie olfattive ufficiali riconosciute dalla Société Française des Parfumeurs,  
bensì alle più numerose sfaccettature olfattive elencate dall’Accademia del Profumo.   

  
 
[^2]:Sebbene per definizione le note di testa siano quelle che si percepiscono immediatamente dopo aver spruzzato il profumo e che costituiscono la prima impressione olfattiva che si ha di un profumo, seguite da cuore e fondo,  
il criterio di ordinamento deve invece, su espressa richiesta del committente, invertire quest’ordine, prediligendo le note di fondo, con pesi proporzionali a quanto descritto.  
Infatti,  
nell'ipotesi in cui il cliente manifesti l'interesse per una specifica nota e gli venga presentato un campione che la manifesta in apertura,   
sussiste il potenziale rischio che il cliente possa essere indotto in errore nell'acquisto di un prodotto che durante l’evoluzione si discosta dalle sue preferenze.  
Al contrario,  
nel caso in cui il cliente mostri apprezzamento per un profumo che,  
pur non presentando necessariamente le caratteristiche richieste già dall’apertura,  
le incorpora gradualmente nel corso della sua evoluzione,  
si può confidare che tale processo risponda in modo più preciso ai gusti specifici espressi.  
Il committente ritiene pertanto che tale approccio determini una maggior soddisfazione della clientela e un incremento degli acquisti conclusi con soddisfazione.  
