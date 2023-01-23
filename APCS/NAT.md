- NAT-enabled router majú jednu alebo viac public IPv4 adries.
- Tieto adresy sa označujú ako NAT pool.
- Keď interné zariadenie pošle traffic von zo siete, NAT router preloží internú IPv4 adresu zariadenia na verejnú adresu z NAT poolu
- NAT router sa väčšinou nachádza na hranici **stub siete**
	- Sieť ktorá ma len 1 exit point na internet
- **Terminológia**
	- **Inside address** - Adresa zariadenia, ktorá je prekladaná pomocou NAT
	- **Outside address** - Adresa cieľového zariadenia
	- **Local address** - Hocijaká adresa, ktorá sa nachádza vo vnútri siete
	- **Gloabl address** - Hocijaká adresa, ktorá sa nachádza mimo siete

# STATIC NAT
- 1 k 1 mapovanie
- Užitočné ak chceme pristupovať k zariadeniu z vonku
- Static NAT table
- Je potrebné mať toľko public adries, koľko je zariadení, ktoré chceme prekladať

# DYNAMIC NAT
- Využíva *pool* public adries a priradzuje ich - prvý príde, prvý berie 
- Je potrebné toľko verejných adries, koľko zariadení pristupuje naraz k internetu

# PAT
- **port address translation**
- Tiež známe ako *overload*
- Mapuje viacero privátnych IP adries k jednej alebo zopár verejným adresám
- Keď NAT router dostane packet od klienta, použije zdrojový port aby unikátne identifikovalo špecifické NAT preloženie 

![[Pasted image 20230123181056.png]]


- Niektoré packety neobsahujú Layer 4 port, napr ICMPv4 správy
- Každý z týchto protokolov je inak handlovany pomocou PAT
- Napr ICMPv4 query správy, echo requesty a echo odpovede majú Query ID

# Výhody nevýhody NAT
-   