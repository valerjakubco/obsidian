- Protokol používaný na *logovanie* udalostí na zariadení, napr. zapnutie/vypnutie rozhrania alebo rozhrania na susedovi, reštartovanie systému a pod.
- Log správy môžu byť zobrazené v reálnom čase v CLI zariadenia alebo uložené v pamäti zariadenia
- Industry standard protokol
- **Syslog message format**
	- *seq:time stamp: %facility-severity-MNEMONIC:description*
	- *seq* - infikuje poradie/sekvenciu správ
	- *time stamp* - čas vygenerovanej správy
	- *facility* - indikuje, ktorý proces na zariadení vygeneroval správu
	- *severity* - dôležitosť eventu, 8 levelov
	- *MNEMONIC* - krátky kód, ktorý indikuje, čo sa stalo
	- *description* - Detailný popis, čo sa vlastne stalo
	- **Levely severity**
		![[Pasted image 20230121174242.png]]

	- **Príklad správy**
		![[Pasted image 20230121174406.png]]

- **Lokácie logov**
	- **Console line** 
		- Zobrazené v CLI
		- Defaultne všetky správy (level 0-7) sú zobrazené
	- **VTY lines**
		- Zobrazené v CLI, keď je zariadenie pripojené cez Telnet/SSH
		- Defaultne vypnuté
	- **Buffer**
		- Správy uložené do RAM
		- Defaultne všetky správy (level 0-7) 
		- Dajú sa zobraziť s *show logging*
	- **Externý server** 
		- Syslog servery počúvajú na *UDP porte 514*
