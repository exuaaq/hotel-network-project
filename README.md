# Hotel Network Infrastructure Project

## Overview
Ovaj projekt predstavlja implementaciju kompletne mrežne infrastrukture za hotelski objekat korištenjem Cisco Packet Tracer-a. Fokus je na segmentaciji mreže pomoću VLAN-ova, dinamičkom rutiranju OSPF protokolom, automatizaciji IP dodjele putem DHCP-a i sigurnom udaljenom pristupu preko SSH-a. 

Cilj je osigurati skalabilnu, sigurnu i lako upravljivu mrežu pogodnu za enterprise okruženje.

---

## Topology Description
Mrežna arhitektura obuhvata tri sprata hotela. Svaki odjel nalazi se u vlastitom VLAN-u i mrežnom segmentu. Ruteri povezuju sve VLAN-ove koristeći OSPF kao dinamički protokol rutiranja.

U topologiji su implementirani:
- Više Layer 2 switcheva
- Više rutera povezanih point-to-point linkovima (/30 mreže)
- DHCP za svaki VLAN
- SSH za sigurno administriranje
- Test PC za verifikaciju udaljenog pristupa i rutiranja

---

## VLAN & IP Address Plan

### **1. Sprat**
| Odjel       | VLAN | Mreža              |
|-------------|------|--------------------|
| Reception   | 80   | 192.168.8.0/24     |
| Store       | 70   | 192.168.7.0/24     |
| Logistics   | 60   | 192.168.6.0/24     |

### **2. Sprat**
| Odjel    | VLAN | Mreža              |
|----------|------|--------------------|
| Finance  | 50   | 192.168.5.0/24     |
| HR       | 40   | 192.168.4.0/24     |
| Sales    | 30   | 192.168.3.0/24     |

### **3. Sprat**
| Odjel | VLAN | Mreža              |
|-------|------|--------------------|
| Admin | 20   | 192.168.2.0/24     |
| IT    | 10   | 192.168.1.0/24     |

---

## Inter-Router Links (/30 Networks)

| Link           | Mreža          |
|----------------|----------------|
| R1 ↔ R2        | 10.10.10.0/30  |
| R2 ↔ R3        | 10.10.10.4/30  |
| R3 ↔ R1        | 10.10.10.8/30  |

**Zašto /30?**
- Dvije usable adrese → savršeno za point-to-point
- Minimum IP potrošnje
- Jasna organizacija i troubleshooting

---

## Implemented Technologies

### **1. VLAN Segmentation**
- Svaki odjel izolovan vlastitim VLAN-om  
- Smanjen broadcast domen  
- Povećana sigurnost i kontrola

### **2. OSPF Dynamic Routing**
- Brza konvergencija  
- Automatsko prilagođavanje promjenama  
- Optimalan izbor ruta

### **3. DHCP**
- Svaki ruter je DHCP server za svoj VLAN  
- Automatska IP dodjela  
- Minimizacija grešaka u konfiguraciji

### **4. SSH Secure Access**
- Siguran, enkriptovan pristup mrežnim uređajima  
- Omogućeno udaljeno upravljanje  
- Testirano preko Test PC-a

---

## Functional Testing

Testovi uključuju:
- Inter-VLAN ping komunikaciju  
- OSPF rute (`show ip route ospf`)  
- DHCP dodjelu (`ip dhcp binding`)  
- SSH konekciju na rutere  
- Test PC verifikaciju udaljenog pristupa

Sve funkcionalnosti su uspješno potvrđene.

---

## How to Use the Project

1. Otvoriti fajl u Cisco Packet Tracer-u.  
2. Pregledati konfiguracije rutera i switcheva putem CLI-ja.  
3. Testirati mrežnu povezanost pomoću ping-a.  
4. Testirati SSH preko Test PC-a:  
   ```
   ssh admin@<router-ip>
   ```  
5. Izmijeniti ili nadograditi topologiju po potrebi.

---

## Conclusion
Projekt demonstrira sposobnost dizajna i implementacije realnog enterprise mrežnog okruženja. Korištenjem VLAN-ova, OSPF-a, DHCP-a i SSH-a postignuta je sigurnost, skalabilnost i efikasnost cijele mreže.


---

