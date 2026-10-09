# Microsoft Intune — Gestion d'un poste Windows 11

## Présentation

Ce laboratoire présente la mise en place et l'administration d'un poste **Windows 11 Pro** avec **Microsoft Intune** dans un environnement de test NovaTech.

L'objectif est de pratiquer plusieurs tâches courantes d'administration moderne d'un poste de travail :

- Enrôlement d'un appareil dans Microsoft Intune
- Microsoft Entra Join
- Déploiement de stratégies de configuration
- Contrôle de la conformité
- Déploiement d'applications
- Administration à distance
- Synchronisation des stratégies et applications

---

## Environnement du laboratoire

| Élément | Configuration |
|---|---|
| Poste client | Windows 11 Pro |
| Virtualisation | VirtualBox |
| Gestion des appareils | Microsoft Intune |
| Identité | Microsoft Entra ID |
| Utilisateur de test | Sophie Martin |
| Appareil | WINDOWS11PRO-UN |

---

# 11. Microsoft Intune

## 11.1 — Enrôlement du poste Windows 11 Pro

Le poste **WINDOWS11PRO-UN** a été intégré à Microsoft Intune afin de permettre son administration depuis le centre d'administration.

Après l'enrôlement, l'appareil apparaît dans Intune avec son utilisateur principal et son état de conformité.

![Enrôlement du poste](images/11.1.png)

---

## 11.2 — Vérification du Microsoft Entra Join

La commande suivante permet de vérifier l'état d'intégration du poste :

`dsregcmd /status`

Le résultat confirme notamment :

- `AzureAdJoined : YES`
- `DomainJoined : NO`

Le poste est donc **Microsoft Entra Joined**.

![Vérification Entra Join](images/11.2.png)

---

## 11.3 — Déploiement d'une stratégie de configuration

Une stratégie de configuration a été créée depuis le **catalogue des paramètres Intune**.

Le paramètre suivant a été activé :

`Prohibit access to Control Panel and PC settings (User)`

L'objectif est d'empêcher l'utilisateur d'accéder au Panneau de configuration du poste.

![Stratégie de configuration](images/11.3.png)

---

## 11.4 — Vérification de la stratégie

Après application de la stratégie, une tentative d'ouverture du Panneau de configuration est bloquée par Windows.

Cette vérification permet de confirmer qu'une configuration définie dans Intune peut être appliquée à distance sur un poste géré.

![Vérification de la stratégie](images/11.4.png)

---

## 11.5 — Stratégie de conformité Windows

Une stratégie de conformité a été créée afin de contrôler l'état de sécurité du poste.

Dans ce laboratoire, la présence du **pare-feu Windows actif** est définie comme obligatoire.

Le poste **WINDOWS11PRO-UN** est ensuite remonté dans Intune avec l'état :

**Conforme**

![Conformité Windows](images/11.5.png)

---

## 11.6 — Déploiement d'une application

L'application **VLC Media Player** a été ajoutée depuis le Microsoft Store puis affectée au poste via Intune.

Après synchronisation, l'application est installée sur Windows 11.

Intune permet ensuite de vérifier à distance l'état du déploiement :

**Installed — 1 appareil**

![Déploiement VLC](images/11.6.png)

---

## 11.7 — Redémarrage à distance

Microsoft Intune permet également d'exécuter certaines actions administratives à distance.

Une commande de **redémarrage** a été envoyée à `WINDOWS11PRO-UN`.

L'utilisateur reçoit une notification avant que Windows exécute le redémarrage demandé par l'administrateur.

![Redémarrage à distance](images/11.7.png)

---

## 11.8 — Synchronisation à distance

Une synchronisation du poste a été déclenchée directement depuis Intune.

Cette opération permet au poste de contacter le service Intune et de traiter les éléments qui lui sont affectés, notamment :

- Stratégies
- Applications
- Scripts

Le portail confirme ensuite le bon déroulement de la synchronisation.

![Synchronisation Intune](images/11.8.png)

---

# Compétences mises en pratique

Ce laboratoire m'a permis de travailler sur :

- Administration de Microsoft Intune
- Gestion d'un poste Windows 11
- Microsoft Entra Join
- Enrôlement et gestion MDM
- Création et affectation de stratégies
- Configuration des postes utilisateurs
- Stratégies de conformité
- Contrôle du pare-feu Windows
- Déploiement d'applications Microsoft Store
- Synchronisation MDM
- Administration et actions à distance
- Diagnostic du déploiement de stratégies

---

## Conclusion

Ce laboratoire reproduit plusieurs opérations pouvant être réalisées par un technicien support ou systèmes dans un environnement Microsoft moderne.

Il permet de comprendre le cycle de gestion d'un poste avec Intune : **enrôler l'appareil, appliquer des configurations, contrôler sa conformité, déployer des applications et effectuer des actions d'administration à distance.**
