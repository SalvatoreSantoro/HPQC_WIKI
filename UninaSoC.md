# UninaSoC build system

Breve introduzione di cos'è UninSoC con spiegazione dello scopo
di didattica che c'è alla base delle modifiche e delle aggiunte apportate al progetto.

Breve introduzione a come funzionano alcuni dei meccanismi di build dei quali
mi sono interessato e fatto uso per andare ad integrare le nuove aggiunte,
quindi di come UninaSoC effettua la compilazione degli "examples" in modo
da permettere l'esecuzione di codice sulla piattaforma e di come vengono generati
i principali file di configurazione per la parte software
(quindi linker script e uninasoc_config.h da me implementato)
con riferimento alla documentazione relativa per vari dettagli aggiuntivi:

https://github.com/SalvatoreSantoro/UninaSoC/blob/feature/HAL/config/README.md  
https://github.com/MaistoV/UninaSoC/blob/main/sw/SoC/README.md  

# UninaSoC for students: a new backend for risc-v_hands_on

## Integration

Parlare di come funziona la fase di integrazione che ho fatto, quindi spiegazione
a grandi linee del makefile di installazione ed esecuzione degli esempi
e di come ho adattato il codice ad utilizzare la printf di tinyIO

## UART and GDB

Parlare brevemente di com'è possibile ora grazie a questa aggiunta
far girare gli stessi esempi precedenti di risc-v_hands_on su un processore fisico
e quindi di come utilizzare l'emulatore di terminale e GDB per eseguire gli esempi


# PLIC and RISC-V Interrupts

piccolo approfondimento sul PLIC e sul vettore delle interrupt di RISC-V
utile anche ad introdurre come l'HAL gestisce le interrupt e cosa mette
a disposizione per ridefinire gli handler

## RISC-V interrupts
1- Parlare dei registri mtvec, mstatus e mie, e come sono configurati nella routine
di startup di UninaSoC in modo da configurare le interruzioni  
2- Parlare di com'è organizzato il vettore delle interruzioni e di come RISC-V
riesce ad identificare i diversi tipi di interruzioni (esterne, software e timer)
in modo da chiamare la ISR giusta  

## PLIC
1- Parlare del PLIC in generale, come funziona e come si configura e utilizza  
2- Parlare di com'è attualmente configurato e usato in UninaSoC  

# Designing an HAL for UninaSoC

## Use cases

1- Parlare del fatto che l'HAL è pensato per essere minimale, ben commentata
e facilmente estendibile in modo da poter essere utilizzata a scopo didattico
per sperimentare con i meccanismi di gestione delle interrupt su RISC-V  
2- Parlare della compilazione modulare per ridurre i tempi di compilazione e
la dimensione dei binari, attraverso file di configurazione opportunamente generato  
3- Parlare della generalizzazione delle API in modo da accomodare futuri espansioni e
aggiunte di nuove copie di periferiche già esistenti, es gpio o timer o cambi di configurazione
in generale.  

## Design Principles

1- Struttura del singolo header "uninasoc.h" per avere una interfaccia semplice  
2- Parlare di come avviene la generazione del file "uninasoc_config.h" e di come esso
influenza le fasi di compilazione  
3- Parlare di come l'indirizzo base di ogni periferica è ottenuto attravero simboli
creati dal linker script generato, il che permette all HAL di riadattarsi automaticamente
in caso di cambio della mappa della memoria del sistema  
4- Parlare della gestione degli errori durante la configurazione delle periferiche
in modo da facilitare il debugging e lo sviluppo  

## Example of use

Breve esempio di utilizzo dell'HAL e della gestione delle interruzioni attraverso
spiegazione dell'esempio delle interrupts  

## Future Developments

In generale si può parlare delle parti della HAL da riadattare o estendere
nel momento in cui si aggiungono nuove periferiche o si rende il PLIC configurabile
dinamicamente  
