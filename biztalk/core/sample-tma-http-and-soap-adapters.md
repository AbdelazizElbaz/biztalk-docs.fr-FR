---
title: "Exemple de menaces : Adaptateurs HTTP et SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- DFD, HTTP adapters
- security examples [TMA], SOAP adapters
- SOAP adapters, examples
- security examples [TMA], HTTP adapters
- examples, HTTP adapters
- DFD, SOAP adapter
- examples, SOAP adapters
- SOAP adapters, TMA
- HTTP adapters, TMA
ms.assetid: d9a40cff-92a1-4bc9-ae45-3a5857f70222
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fedbdd03e79a0a9250b184695806813f2805e34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-http-and-soap-adapters"></a>Exemple de menaces : Adaptateurs HTTP et SOAP
Cette rubrique présente l'analyse du modèle des menaces pour le scénario des adaptateurs HTTP et SOAP (services Web) dans un exemple d'architecture. La figure suivante illustre l'exemple d'architecture pour le scénario des adaptateurs HTTP et SOAP.  
  
 **Figure 1 exemple d’architecture pour le scénario des adaptateurs HTTP/SOAP**  
  
 ![Exemple d’architecture pour l’adaptateur HTTP ou SOAP](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")  
  
## <a name="step-1-collect-background-information-http-and-soap-adapters-scenario"></a>Étape 1. Collecter des informations générales (scénario des adaptateurs HTTP et SOAP)  
 Cette section présente le diagramme de flux de données pour le scénario des adaptateurs HTTP et SOAP (services Web) dans un exemple d'architecture.  
  
 Toutes les autres informations d’arrière-plan est le même pour tous nos scénarios d’utilisation et est décrite précédemment dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
### <a name="data-flow-diagram"></a>Diagramme de flux de données  
 La figure suivante illustre le diagramme de flux de données pour l'exemple d'architecture lors de l'utilisation des adaptateurs HTTP et SOAP (services Web).  
  
 **Figure 2 DFD pour l’exemple d’architecture du scénario de l’adaptateur HTTP/SOAP**  
  
 ![DFD pour l’exemple d’architecture](../core/media/tdi-sec-refarch-dfd-http.gif "TDI_Sec_RefArch_DFD_HTTP")  
  
 Le flux de données est le suivant :  
  
1.  Un partenaire ou un client envoie un message via HTTP, HTTPS ou un service Web. Ce message est acheminé à l'adresse IP du pare-feu 1.  
  
2.  Le pare-feu 1 relaie le message via le pare-feu 2 à l'aide du proxy inverse.  
  
3.  Le pare-feu 2 achemine le message au serveur BizTalk Server qui exécute une instance d'un hôte isolé pour l'adaptateur de réception HTTP ou SOAP. L'hôte isolé traite le message et place celui-ci dans la base de données MessageBox.  
  
4.  Une instance de l'hôte de traitement, qui a un abonnement au message, le récupère dans la base de données MessageBox, effectue un traitement supplémentaire, puis replace le message dans la base de données MessageBox.  
  
5.  Une instance de l'hôte isolé, qui a un adaptateur d'envoi HTTP ou SOAP, récupère le message dans la base de données MessageBox. Le message passe par un traitement final dans le pipeline d'envoi, puis est renvoyé au partenaire ou au client.  
  
6.  Étant donné que le message est envoyé au partenaire ou au client, il est acheminé via le pare-feu 2 et via le pare-feu 1 à l'aide du proxy inverse.  
  
## <a name="step-2-create-and-analyze-the-threat-model-http-and-soap-adapters-scenario"></a>Étape 2. Créer et analyser le modèle des menaces (scénario des adaptateurs SOAP et HTTP)  
 Cette section présente les résultats de l'analyse du modèle des menaces pour le scénario des adaptateurs HTTP et SOAP (services Web) dans un exemple d'architecture.  
  
-   **Identifier les Points d’entrée, les limites de confiance et les flux de données -** consultez des informations générales décrites précédemment à l’étape 1 et [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
-   **Créer une liste des menaces identifiées -** nous avons utilisé la catégorisation suivante pour toutes les entrées du diagramme pour identifier les menaces potentielles pour le scénario : **S**urpation identifier, **T** ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges. Le tableau suivant répertorie les menaces qui ont été identifiées lors de l'utilisation des adaptateurs HTTP et SOAP pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 1 liste des menaces**  
  
|Menace| Description|Actif|Impact|  
|------------|-----------------|-----------|------------|  
|Envoi d'un message de taille infinie|Un utilisateur malveillant peut envoyer un message de taille infinie.|Environnement BizTalk Server|Déni de service|  
|Envoi d'un grand nombre de messages à l'emplacement de réception|Un utilisateur malveillant peut envoyer un grand nombre de messages valides ou non valides et inonder l'application.|Environnement BizTalk Server|Déni de service|  
|Lecture de corps de messages via HTTP|Un utilisateur malveillant peut intercepter et lire un message alors que celui-ci transite entre l'expéditeur et le pare-feu 1.|Charge du message|Divulgation d'informations|  
|Lecture d'informations d'identification à partir d'un message|Si vous faites appel à l'authentification de base et que le message contient des informations d'identification, un utilisateur malveillant peut obtenir l'accès à ces informations d'identification et les utiliser pour accéder à l'application.|Informations d’identification de l’utilisateur|Divulgation d'informations<br /><br /> Élévation de privilèges|  
  
## <a name="step-3-review-threats-http-and-soap-adapters-scenario"></a>Étape 3. Examen des menaces (scénario des adaptateurs SOAP et HTTP)  
 Cette section présente les résultats de l'analyse des risques réalisée sur les menaces identifiées pour le scénario des adaptateurs HTTP et SOAP (services Web) dans un exemple d'architecture. Après la principale menace réunion sur le modèle, nous avons passé en revue les menaces et les catégories d’impact suivants permettent d’identifier les risques pour chaque menace : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **A**tteinte des utilisateurs et **D**étectabilité.  
  
 Le tableau suivant répertorie les degrés de risque pour les menaces qui ont été identifiées lors de l'utilisation des adaptateurs HTTP et SOAP pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 2 degrés de risque de menaces**  
  
|Menace|Impact|Dégâts potentiels|Reproductibilité|Exploitabilité|Atteinte des utilisateurs|Détectabilité|Exposition au risque|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|Envoi d'un message de taille infinie|Déni de service|2|3|2|3|2|2.4|  
|Envoi d'un grand nombre de messages à l'emplacement de réception|Déni de service|3|3|1|3|3|2.6|  
|Lecture de corps de messages via HTTP|Divulgation d'informations|3|3|2|3|3|2.8|  
|Lecture d'informations d'identification à partir d'un message|Divulgation d'informations<br /><br /> Élévation de privilèges|3|3|2|3|2|2.6|  
  
## <a name="step-4-identify-mitigation-techniques-http-and-soap-adapters-scenario"></a>Étape 4. Identifier les Techniques de prévention (scénario des adaptateurs SOAP et HTTP)  
 Cette section présente certaines techniques de prévention des menaces identifiées pour le scénario des adaptateurs HTTP et SOAP (services Web) dans un exemple d'architecture.  
  
 Le tableau suivant répertorie les techniques et technologies de prévention des menaces qui ont été identifiées lors de l'utilisation des adaptateurs HTTP et SOAP pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 3 techniques de prévention et technologies**  
  
|Menace|Impact|Exposition au risque|Techniques et technologies de prévention|  
|------------|------------|-------------------|--------------------------------------------|  
|Envoi d'un message de taille infinie|Déni de service|2.4|Limitez la taille maximale, par URL, d'un message entrant et rejetez les messages dépassant cette valeur maximale.<br /><br /> Pour plus d’informations, consultez [atténuation des attaques par déni de Service](../core/mitigating-denial-of-service-attacks.md).|  
|Envoi d'un grand nombre de messages à l'emplacement de réception|Déni de service|2.6|L'adaptateur SOAP exploite le protocole HTTP pour envoyer et recevoir des messages vers et depuis BizTalk Server. Par conséquent, vous devez suivre les recommandations en matière de sécurité pour sécuriser IIS (Internet Information Services). Si vous utilisez IIS, veillez à suivre les recommandations correspondantes ayant trait à la configuration de l'isolement d'une application.<br /><br /> Pour plus d’informations, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=60951](http://go.microsoft.com/fwlink/?LinkId=60951).<br /><br /> Utilisez les fonctionnalités d'authentification du client et de résolution de tiers pour limiter le nombre de messages traités à ceux étant valides et approuvés.|  
|Lecture de corps de messages via HTTP|Divulgation d'informations|2.8|Il est recommandé d'utiliser S/MIME pour sécuriser le contenu des messages envoyés vers et depuis BizTalk Server.<br /><br /> Il est également conseillé d'utiliser le protocole SSL (Secure Sockets Layer) pour sécuriser la transmission des données vers et depuis BizTalk Server ainsi qu'entre les composants BizTalk Server distribués au sein de votre environnement.|  
|Lecture d'informations d'identification à partir d'un message|Divulgation d'informations<br /><br /> Élévation de privilèges|2.6|Lorsque vous utilisez l'authentification de base, ou lorsque vous n'utilisez pas le chiffrement au niveau du message, il est fortement conseillé d'utiliser SSL pour envoyer et recevoir des messages afin de vous assurer qu'aucune personne non autorisée ne puisse lire vos informations d'identification.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse du modèle](../core/threat-model-analysis.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)