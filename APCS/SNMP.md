  - *Simple Network Management Protocol*
- 2 typy hlavných zariadení:
	- *Managed Devices*
		 - Tieto zariadenia sú manažované SNMP
	 - *Network Management Station*
		 - SNMP server

- **SNMP Operácia**
	1. *Managed devices* môžu notifikovať NMS o *udalostiach*, napr. vypnuté rozhranie
	2. *NMS* môže požadovať informácie od *Managed Devices* o ich aktuálnom stave
	3. *NMS* môže povedať *managed devices* aby zmenili aspekty konfigurácie
	![[snmp_operacie.png]]

**Komponenty SNMP**
- **NMS**
		- SNMP Manager
			- Software na NMS, ktorý interaguje s "managed" zariadeniami
			- Dostáva notifikácie, posiela requesty pre informácie, posiela zmeny konfigurácií atď.
		- SNMP Aplikácia
			- Poskytuje rozhranie pre sieťového admina na interakciu
			- Zobrazuje výstrahy, štatistiky, tabuľku a pod.
	- **Managed device**
		- SNMP Agent
			- Software bežiaci na zariadení, ktorý interaguje s *SNMP* managerom na *NMS*
			- Posiela notifikácie alebo prijíma správy z *NMS*
		- Management Information Base (MIB)
			- Štruktúra, ktorá obsahuje *premenné* manažované SNMP
			- Každá premenná je identifikovaná s *Object ID*
			- Stav rozhrania, throughput, CPU usage, teplota atď.

 - **Object IDs**
	- Sú organizované v hierarchickej štruktúre
- **Verzie SNMP**
	 - **SNMPv1**
		- Originálna verzia SNMP
	 - **SNMPv2c**
		- Povoľuje NMS aby získalo veľké množstvá informácia v jednom requeste, je to viac efektívne
		- **c** referuje na *community strings* používané ako heslá v SNMPv1, odstránené z SNMPv2 a pridané naspať pre SNMPv2c
	 - **SNMPv3**
		- Oveľa bezpečnejšia verzia SNMP
		- Podporuje silnú **enkrypciu** a **autentifikáciu**
		- Mala by byť používaná vždy, keď je to možné

 - **SNMP Správy**
	![[snmp_spravy.png]]