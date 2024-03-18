# **VPN-MPLS** 

<figure>
  <img src="https://github.com/ApprentiBash/PFE-VPNMLPS/blob/main/TEST-LAB-VPNMPLS/screen/2024-03-08_18h00_34.png?raw=true" alt="Schéma structurel du Lab EVE-NG">
  <figcaption>Figure 1 : Schéma structurel du Lab EVE-NG</figcaption>
</figure>

____
## **Contexte** 
Dans le cadre du projet de fin d'étude, nous entreprenons la conception et la mise en œuvre d'une architecture réseau évoluée, visant à interconnecter de manière sécurisée et efficace plusieurs réseaux d'entreprise distincts. 
Ce projet, centré sur l'utilisation de la technologie Multi-Protocol Label Switching (MPLS), vise à établir un réseau privé virtuel (VPN) capable de connecter cinq sites d'entreprise distincts.

Actuellement, nous amorçons cette initiative en démarrant avec l'interconnexion de deux sites d'entreprise. 
Les routeurs d'entreprise (CE) R1-CE-MPLS et R8-CE-MPLS représentent ces deux sites initiaux. Ce laboratoire pose les fondations nécessaires pour l'architecture MPLS VPN complète. 
Chaque site d'entreprise fonctionne comme une entité autonome, avec ses propres réseaux locaux et ses besoins spécifiques en matière de sécurité et de connectivité.
____
## **Objectif** 
L'objectif principal de ce lab est de créer avec succès une architecture MPLS VPN interconnectant deux sites d'entreprise. 
Il s'agit de la première étape d'un projet plus vaste. 
Les tâches spécifiques comprennent la configuration des protocoles de routage (OSPF, BGP) et de MPLS sur les routeurs, 
la définition d'instances VRF pour assurer l'isolation des réseaux d'entreprise, et l'établissement de sessions BGP entre les routeurs de fournisseur de services (PE).
____
## **Routeur** 

Résumé global de la configuration des routeurs et explication de leur rôle :

**R1-CE-MPLS-OSPF:**

Objectif : Routeur d'entreprise connecté au réseau MPLS.
Configuration : Définit des interfaces pour le réseau d'entreprise, active OSPF pour l'échange de routes, et redistribue les routes connectées dans OSPF.

**R2-PE-MPLS:**

Objectif : Routeur de fournisseur de services (PE) pour le site_A.
Configuration : Configure une interface VRF, active MPLS, BGP, et OSPF pour le site_A. Établit des sessions BGP avec d'autres routeurs PE.

**R3-PE-MPLS:**

Objectif : Routeur de fournisseur de services (PE) pour le site_A.
Configuration : Similaire à R2, mais connecté au site_A. Établit des sessions BGP avec d'autres routeurs PE.

**R4-BGP-MPLS:**

Objectif : Routeur de bord BGP connecté au réseau MPLS.
Configuration : Active MPLS, BGP, et OSPF. Annonce des réseaux via OSPF et les redistribue dans BGP.

**R5-BGP-MPLS:**

Objectif : Routeur de bord BGP connecté au réseau MPLS.
Configuration : Similaire à R4, mais annonce des réseaux différents via OSPF.

**R6-PE-MPLS:**

Objectif : Routeur de fournisseur de services (PE) pour le site_B.
Configuration : Similaire à R2, mais connecté au site_B. Établit des sessions BGP avec d'autres routeurs PE.

**R7-PE-MPLS:**

Objectif : Routeur de fournisseur de services (PE) pour le site_B.
Configuration : Similaire à R6, mais connecté au site_B. Établit des sessions BGP avec d'autres routeurs PE.

**R8-CE-MPLS-OSPF:**

Objectif : Routeur d'entreprise connecté au réseau MPLS.
Configuration : Similaire à R1, mais connecté au site_B.

### **Remarques :**

- Les routeurs de fournisseurs de services (PE) gèrent les instances VRF pour les sites_A et_B.
- MPLS est utilisé pour créer des tunnels entre les PE et permettre une connectivité VPN.
- BGP est utilisé pour échanger des informations de routage entre les routeurs PE et pour annoncer des réseaux externes.
- OSPF est utilisé pour l'échange de routes internes à chaque site.
