# -AA2-Avaluaci-An-lisis-Kea-DHCP
## Bloc 1: Fonaments del Protocol i Anàlisi de Tràfic (Wireshark / tcpdump)

1. Procés de Negociació (DORA):

- Descriu la funció dels quatre missatges del cicle DHCP (Discover, Offer, Request, Acknowledge).

**El discover es cuan la persona envia un misatge i el dhcp busca una xarxa disponigle.**

**El Offer es cuan el dhcp dona una ip disponible per la xarxa.**


**La request es cuan el la persona envia un misatge per saber quine es el servidor i ip que utilizara.**


**El Acknowleadge es cuan el dhcp confirma la ip que pot utilizar el ordinador per enviar el missatge**

- Indica quines d'aquestes fases es realitzen mitjançant missatges de tipus Broadcast i quines en Unicast en un entorn local sense DHCP Relay.

2. Captura i Capçaleres de Paquet:

- Especifica els ports UDP font i destí utilitzats pel client i pel servidor DHCP.

- Quin camp de la capçalera DHCP s'utilitza per identificar unívocament la targeta de xarxa (NIC) del client?

- Identifica el número o nom de les Opcions DHCP (DHCP Options) encarregades de transmetre la porta d'enllaç per defecte (Router), els servidors DNS i el nom de domini.

## Bloc 2: Configuració del Servidor Kea DHCP (kea-dhcp4.conf)
Redacta l'estructura del fitxer de configuració JSON per al dimoni kea-dhcp4 complint els requisits següents:

Interfície i Emmagatzematge:

Configuració de la interfície de xarxa eth0.

Model de base de dades de cessions en memòria (memfile) amb persistència activada.

Paràmetres Globals i de Temps:

Temps de cessió (valid-lifetime): 2 hores (7200 segons).

Temps de renovació (renew-timer): 1 hora (3600 segons).

Subxarxa i Pool Dinàmic:

Adreça de xarxa: 192.168.x.0/24.

Rang d'adreces dinàmiques assignables (pool): Des de la 192.168.x.50 fins a la 192.168.x.200.

Opcions de Xarxa (option-data):

Encaminador / Porta d'enllaç: 192.168.x.1.

Servidors DNS primari i secundari: 1.1.1.1 i 8.8.8.8.

Nom de domini local: oficina.local.

## Bloc 3: Assignació Estàtica (Reserves per Adreça MAC)
Afegeix la secció de reserves (reservations) dins de la configuració de la subxarxa per garantir una adreça IP fixa a una impressora de xarxa de l'oficina:

Paràmetres de la reserva:

Adreça MAC de la targeta (hw-address): aa:bb:cc:11:22:33.

Adreça IP assignada: 192.168.x.20.

Nom de l'equip (hostname): impresora-dir.

Validació de Sintaxi:

Indica quines eines o comandes utilitza Kea o el sistema per comprovar que el fitxer JSON no conté errors de sintaxi abans d'iniciar el servei.

## Bloc 4: Comprovació, Diagnòstic i Resolució d'Incidències
Comprovacions al Servidor:

Quines comandes de systemctl permeten verificar l'estat, reiniciar o aturar el servei de Kea DHCP?

Mitjançant quines comandes o utilitats del sistema (journalctl / registres) es poden consultar les peticions i incidències del servei Kea?

En quina ruta i quin fitxer emmagatzema Kea la llista de cessions actives (leases) quan s'utilitza el motor memfile?

Proves des del Client:

Especifica les comandes necessàries en un client Linux (dhclient / nmcli / ip) per alliberar la IP actual i sol·licitar-ne una de nova.

Especifica les comandes equivalents en un client Windows (ipconfig).

## Bloc 5: Disseny del Mapa Conceptual del Servei DHCP
Dibuixa o esquematitza un mapa conceptual que connecti visualment tots els components del servei. En el mapa han d'aparèixer obligatòriament els següents conceptes i relacions (sense incloure la seva definició o explicació):

Nivell de Transport i Protocols: Ports UDP (67 i 68), Broadcast vs. Unicast.

Cicle de Vida DHCP: Fases DORA (Discover, Offer, Request, Acknowledge).

Fitxer de Configuració Kea (kea-dhcp4.conf): Paràmetres interfaces-config, lease-database, valid-lifetime, renew-timer, subnet4, pools, option-data i reservations.

Identificació de Dispositius: Adreça MAC (hw-address) i Nom d'host (hostname).

Fitxers de Registre i Gestió: Cessions actives (kea-leases4.csv), dimoni de sistema (kea-dhcp4-server) i registre de logs (journalctl).

Diagnòstic de Xarxa: Captura de paquets (tcpdump / Wireshark) i comandes de client (ipconfig / dhclient).
