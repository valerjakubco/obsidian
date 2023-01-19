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