---
title: "Exemple TMA : Adaptateur de file d’attente de Message BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], MSMQ adapters
- architecture, examples
- MSMQ adapters, TMA
- DFD, MSMQ adapters
- MSMQ adapters, data flow
ms.assetid: 15b4a540-2fcd-4668-b4b4-757f23ebd83e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91f37c57c24bdd37c0f2cc0399a797050228aa54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-biztalk-message-queuing-adapter"></a>Exemple de menaces : Adaptateur Message Queuing BizTalk
Cette rubrique présente l'analyse du modèle des menaces pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.  
  
## <a name="step-1-collect-background-information-biztalk-message-queuing-adapter-scenario"></a>Étape 1. Collecter des informations générales (scénario Message Queuing BizTalk adaptateur)  
 Cette section présente le diagramme de flux de données pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture. La figure suivante illustre l'exemple d'architecture pour le scénario des adaptateurs HTTP et SOAP.  
  
 **Figure 1 exemple d’architecture pour le scénario de l’adaptateur BizTalk Message Queuing**  
  
 ![Exemple d’architecture pour Message Queuing BizTalk](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")  
  
 Toutes les autres informations d’arrière-plan est le même pour tous nos scénarios d’utilisation et est décrite précédemment dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
### <a name="data-flow-diagram"></a>Diagramme de flux de données  
 La figure suivante illustre le diagramme de flux de données pour l'exemple d'architecture lors de l'utilisation de l'adaptateur de Message Queuing BizTalk.  
  
 **Figure 2 DFD pour l’exemple d’architecture du scénario de l’adaptateur de Message Queuing BizTalk**  
  
 ![Exemple d’architecture pour Message Queuing BizTalk](../core/media/tdi-sec-refarch-dfd-msmq.gif "TDI_Sec_RefArch_DFD_MSMQ")  
  
 Le flux de données est le suivant :  
  
1.  Un partenaire envoie un message à l'aide de Message Queuing ou de Message Queuing BizTalk. Le message est converti au format approprié et envoyé sur le réseau. Si vous utilisez Active Directory, le message passe par une série de routeurs Message Queuing jusqu'à atteindre la bonne destination (le serveur BizTalk qui exécute une instance de l'hôte de l'adaptateur de réception Message Queuing BizTalk).  
  
2.  Une instance d'un hôte In-process pour l'adaptateur de réception Message Queuing BizTalk reçoit régulièrement le message d'un routeur Message Queuing (à travers le pare-feu 2), effectue un traitement initial, envoie les réponses correctes du réseau, comme défini par le protocole réseau, puis place le message dans la base de données MessageBox.  
  
3.  Une instance de l'hôte de traitement, qui a un abonnement au message, le récupère dans la base de données MessageBox, effectue un traitement supplémentaire, puis replace le message dans la base de données MessageBox.  
  
4.  Une instance de l'hôte In-process, qui a un adaptateur d'envoi Message Queuing BizTalk, récupère le message dans la base de données MessageBox. Le message passe par un traitement final dans le pipeline d'envoi, puis est envoyé, à travers le pare-feu 2, sur le réseau au partenaire ou à l'application.  
  
## <a name="step-2-create-and-analyze-the-threat-model-biztalk-message-queuing-adapter-scenario"></a>Étape 2. Créer et analyser le modèle des menaces (scénario Message Queuing BizTalk adaptateur)  
 Cette section présente les résultats de l'analyse du modèle des menaces pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.  
  
-   **Identifier les Points d’entrée, les limites de confiance et les flux de données -** consultez les informations générales décrites précédemment à l’étape 1 et dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
-   **Créer une liste des menaces identifiées -** nous avons utilisé la catégorisation suivante pour toutes les entrées du diagramme pour identifier les menaces potentielles pour le scénario : **S**urpation identifier, **T** ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges. Le tableau suivant répertorie les menaces que nous avons identifiées lorsque vous utilisez l'adaptateur de Message Queuing BizTalk pour envoyer et recevoir des messages à et de BizTalk Server.  
  
 **Tableau 1 liste des menaces identifiées**  
  
|Menace| Description|Actif|Impact|  
|------------|-----------------|-----------|------------|  
|Envoi d'un grand nombre de messages à l'emplacement de réception|Un utilisateur malveillant peut envoyer un grand nombre de messages valides ou non valides et inonder l'application.|Environnement BizTalk Server|Déni de service|  
|L'en-tête du message transite en texte clair.|Comme le message transite de la file d'attente à l'adaptateur de réception Message Queuing BizTalk, l'en-tête du message est en texte clair et un utilisateur malveillant peut lire et falsifier l'en-tête.|En-tête du message|Falsification de données<br /><br /> Divulgation d'informations|  
|Un utilisateur non autorisé peut établir une connexion réseau au serveur BizTalk qui exécute l'hôte Message Queuing BizTalk.|Vous ne pouvez pas utiliser de liste de contrôle d'accès discrétionnaire pour limiter l'accès à l'emplacement de réception Message Queuing BizTalk. Par conséquent, toute personne pouvant établir une connexion réseau au serveur BizTalk qui exécute une instance de l'hôte de l'adaptateur de réception Message Queuing BizTalk et au port 1801 peut envoyer des messages à l'emplacement de réception Message Queuing BizTalk.|Environnement BizTalk Server|Répudiation<br /><br /> Falsification de données<br /><br /> Divulgation d'informations<br /><br /> Déni de service<br /><br /> Élévation de privilèges|  
|Un utilisateur malveillant peut falsifier le message avant que BizTalk Server ne le reçoive.|Un utilisateur malveillant peut intercepter le message lorsqu'il transite et le modifier.|Corps du message|Falsification de données<br /><br /> Divulgation d'informations|  
  
## <a name="step-3-review-threats-biztalk-message-queuing-adapter-scenario"></a>Étape 3. Examen des menaces (scénario Message Queuing BizTalk adaptateur)  
 Cette section présente les résultats de l'analyse des risques réalisée sur les menaces identifiées pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture. Après la principale menace réunion sur le modèle, nous avons passé en revue les menaces et les catégories d’impact suivants permettent d’identifier les risques pour chaque menace : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **A**tteinte des utilisateurs et **D**étectabilité.  
  
 Le tableau suivant répertorie les degrés de risque pour les menaces que nous avons identifiées lorsque vous utilisez l'adaptateur de Message Queuing BizTalk pour envoyer et recevoir des messages à et de BizTalk Server.  
  
 **Tableau 2 degrés de risque pour les menaces identifiées**  
  
|Menace|Impact|Dégâts potentiels|Reproductibilité|Exploitabilité|Atteinte des utilisateurs|Détectabilité|Exposition au risque|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|Envoi d'un grand nombre de messages à l'emplacement de réception|Déni de service|8|7|7|7|5|6.8|  
|L'en-tête du message transite en texte clair.|Falsification de données<br /><br /> Divulgation d'informations|8|10|8|3|5|6.8|  
|Un utilisateur non autorisé peut établir une connexion réseau au serveur BizTalk qui exécute l'hôte Message Queuing BizTalk.|Répudiation<br /><br /> Falsification de données<br /><br /> Divulgation d'informations<br /><br /> Déni de service<br /><br /> Élévation de privilèges|8|10|9|9|9|9|  
|Un utilisateur malveillant peut falsifier le message avant que BizTalk Server ne le reçoive.|Falsification de données<br /><br /> Divulgation d'informations|5|7|6|5|7|6|  
  
## <a name="step-4-identify-mitigation-techniques-biztalk-message-queuing-adapter-scenario"></a>Étape 4. Identifier les Techniques de prévention (scénario Message Queuing BizTalk adaptateur)  
 Cette section présente certaines techniques de prévention des menaces identifiées pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.  
  
 Le tableau suivant répertorie les techniques et technologies de prévention des menaces que nous avons identifiées lorsque vous utilisez l'adaptateur de Message Queuing BizTalk pour envoyer et recevoir des messages à et de BizTalk Server.  
  
 **Tableau 3 techniques de prévention et technologies**  
  
|Menace|Impact|Exposition au risque|Techniques et technologies de prévention|  
|------------|------------|-------------------|--------------------------------------------|  
|Envoi d'un grand nombre de messages à l'emplacement de réception|Déni de service|6.8|Utilisez l'adaptateur de Message Queuing BizTalk en mode à authentification requise. Définir le **authentification MSMQ requise** indicateur sur l’emplacement de réception et **authentification requis (abandonner les messages)** sur le port de réception.<br /><br /> Configurez Message Queuing BizTalk pour qu'il exige une authentification basée sur un certificat. Ce comportement se produit au niveau de l'adaptateur et est différent du composant Résolution du tiers d'un pipeline BizTalk. Si configuré, le certificat public est inclus avec le message entrant. C'est le seul mode d'authentification client disponible pour Message Queuing BizTalk. Pour l'utiliser, vous devez installer Message Queuing BizTalk en mode d'intégration Active Directory. Lorsque vous utilisez cette fonctionnalité, n’oubliez pas de sélectionner le **exiger une authentification** emplacement de réception de case à cocher dans la boîte de dialogue Propriétés de Message Queuing BizTalk.|  
|L'en-tête du message transite en texte clair.|Falsification de données<br /><br /> Divulgation d'informations|6.8|Utilisez la sécurité du protocole Internet (IPSec) pour protéger le corps et l'en-tête du message lorsqu'il transite d'un serveur à l'autre.|  
|Un utilisateur non autorisé peut établir une connexion réseau au serveur BizTalk qui exécute l'hôte Message Queuing BizTalk.|Répudiation<br /><br /> Falsification de données<br /><br /> Divulgation d'informations<br /><br /> Déni de service<br /><br /> Élévation de privilèges|9|Créez un pipeline personnalisé avec un composant de pipeline Résolution de tiers, puis configurez ce dernier pour utiliser l'ID de l'expéditeur (SID) afin de résoudre le tiers. Définir le **résoudre le tiers par certificat** propriété **False**et le **résoudre le tiers par SID** propriété **True**. Pour plus d’informations, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).<br /><br /> Sur le port de réception, définissez la **authentification** propriété **requis (abandonner les Messages)**.|  
|Un utilisateur malveillant peut falsifier le message avant que BizTalk Server ne le reçoive.|Falsification de données<br /><br /> Divulgation d'informations|6|Utilisez l'authentification par protocole pour vous assurer que le message n'a pas été falsifié lors de son transit. Pour l'utiliser, vous devez disposer d'un routeur Message Queuing dans le domaine E-Business. Configurer BizTalk Server comme suit :<br /><br /> -Sur le **messagerie BizTalk** page du Gestionnaire de Configuration, indiquez le nom du routeur.<br />-Pour le port de réception, définissez la **authentification** propriété **requis (abandonner les Messages)** ou **requis (conserver les Messages)**.<br />-Pour le Gestionnaire d’envoi sur le **général** sous l’onglet du **routeur MSMQ** zone Nom, tapez le nom du routeur Message Queuing.<br />-Pour le port d’envoi, sélectionnez **utiliser l’authentification MSMQ**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse du modèle](../core/threat-model-analysis.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)