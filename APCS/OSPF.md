  - Open Shortest Path First
- Využíva Dijkstrov algoritmus
- Existujú 3 verzie
	- OSPFv1 - viac sa už nepoužíva
	- OSPFv2 - používa sa na IPV4
	- OSPFvš - používa sa na IPv6
-  Routre ukladajú informácie o sieti v **LSA (Link State Advertisements)**, tie sú zorganizované v štruktúre **LSDB (Link State Database)**
- Routre zaplavujú LSA tabuľky, dokedy všetky routre v *OSPF area* nemajú rovnakú mapu siete *(LSDB)*

# OSPF proces
 1. Routre sa stanú "neighbors"
 2. Výmena *LSA*
 3. Vypočítanie najlepšej cesty 

# OSPF packety 
**Multiprotocol Label Switching (MPLS)** je technológiou smerovania v telekomunikačných sieťach, ktorá smeruje dáta z jedného uzla na druhý uzol na základe krátkych štítkov (labels), nemá dlhé sieťové adresy, čím sa zabráni zložitému vyhľadávaniu v smerovacej tabuľke a rýchlosti dopravných tokov.

**LSP (Label-switched path)** poskytuje cestu prostredníctvom **MPLS** siete.
**Typy LSP:**
- Typ 1: **Hello Packet**
	- Objavujú OSPF susedov a vytvárajú neighbor adjacencies (priľahlé susedstvá).
	- propagujú parametre, na ktorých sa musia dva smerovače dohodnúť, aby sa stali susedmi.**Vyberajú spomedzi smerovačov Designated Router (DR)** a **Backup Designated Router (BDR)** v sieťach s viacerými prístupmi, ako je napr.: Ethernet a Frame Relay. OSPF Hello pakety sa prenášajú na multicast adresu 224.0.0.5 vo formáte IPv4 a FF02::5 v protokole IPv6.
- Typ 2: **Database Description (DBD) paket**
	- Kontrola synchronizácie databázy medzi smerovačmi.
- Typ 3: **Link-State Request (LSR) paket**
	-  Vyžaduje konkrétne záznamy o stave prepojenia od smerovača k smerovaču.
- Typ 4: **Link-State Update (LSU) paket**
	- Posiela požadované záznamy o stave prepojenia.
- Typ 5: **Link-State Acknowledgment (LSAck) packet**
	- Potvrdzuje ostatné typy paketov.

# OSPF states
- **Down state**
	- Routre sa zatiaľ navzájom nepoznajú, ale pošlú **Hello packety** z rozhraní
- **Init state**
	- Keď router dostane *Hello packet* od iného routera, ale nie je tam jeho ID ako cieľ
- **2-way state**
	- Router pošle *Hello packet* s ID oboch routerov. Keď router dostane packet so svojim ID, su ready na zdieľanie LSAs aby zostavili spoločnú LSDB. V tomto bode sa vyberá DR a BDR
- **Exstart state**
- **Exchange state**
- **Loading state**
- **Full state**

# OSPF areas
- OSPF využíva areas na rozdelenie siete
- **Area** je súhrn routerov a linkov, ktoré zdieľajú rovnaké LSDB
- **Backbone area** *(area 0)* je area, na ktorú sa ostatné *areas* musia napojiť
	 ![[backbone.png]]
- routre so všetkými rozhraniami v rovnakej *area* sa nazývajú **internal routers** 
- routre s rozhraniami vo viacerých *areas* sa nazývajú **area border routers (ABRs)**
	- ABRs ukladajú rozdielne LSDB pre každú *areu* do ktorej su pripojené. Odporúča sa ABR pripojiť na max. 2 *areas*
- routre pripojené do *backbone area (area 0)* sa nazývajú **backbone routers**
- malé siete môžu byť single area, bez negatívnych efektov na performance
- vo veľkých sieťach to môže mať negatívne efekty 
	- algoritmu trvá dlhšie dokedy vypočíta *routy*
	- algoritmu treba viac *processing power*
	- väčšie LSDBs zaberajú viac pamäte na routeroch
	- každá drobná zmena v sieti zapríčiní každý router aby zase zaplavova LSAs a znova spúšťal SPF algoritmus

# Basic OSPF configuration
![[basic_config_1.png]]
- *passive-interface* hovorí routeru, do ktorých rozhraní neposielať LSAs
- *default-information originate* vytvorí novú LSA pre defaultnu *route*

