---
title: "Exemple de menaces : L’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- examples, FTP adapters
- security examples [TMA], FTP adapters
- FTP adapters, TMA
- DFD, FTP adapters
ms.assetid: c648f84a-c83a-44f0-adc9-a3f98b597506
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88f01eadc2fcadf6592e61b38203bb09e69b547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-ftp-adapter"></a>Exemple de menaces : L’adaptateur FTP
Cette rubrique présente l'analyse du modèle des menaces pour le scénario de l'adaptateur FTP dans un exemple d'architecture.  
  
 L'exemple d'architecture pour le scénario de l'adaptateur FTP est présenté dans le schéma suivant.  
  
 **Figure 1 exemple d’architecture pour le scénario de l’adaptateur FTP**  
  
 ![Exemple d’architecture pour l’adaptateur FTP](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")  
  
## <a name="step-1-collect-background-information-ftp-adapter-scenario"></a>Étape 1. Collecter des informations générales (scénario de l’adaptateur FTP)  
 Cette section présente le diagramme de flux de données pour le scénario de l'adaptateur FTP dans un exemple d'architecture.  
  
 Toutes les autres informations d’arrière-plan est le même pour tous nos scénarios d’utilisation et est décrite précédemment dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
### <a name="data-flow-diagram"></a>Diagramme de flux de données  
 La figure suivante illustre le diagramme de flux de données pour l'exemple d'architecture lors de l'utilisation de l'adaptateur FTP.  
  
 **Figure 2 DFD pour l’exemple d’architecture du scénario de l’adaptateur FTP**  
  
 ![DFD pour l’adaptateur FTP](../core/media/tdi-sec-refarch-dfd-ftp.gif "TDI_Sec_RefArch_DFD_FTP")  
  
 Le flux de données est le suivant :  
  
1.  Un partenaire ou un client envoie un message au serveur FTP. Ce message est acheminé à l'adresse IP du pare-feu 1.  
  
2.  Le pare-feu 1 reçoit le message et l'achemine au serveur FTP, lequel est situé dans le réseau de périmètre Internet.  
  
3.  Une instance d'un hôte In-process pour l'adaptateur de réception FTP interroge régulièrement le serveur FTP pour les nouveaux messages (à travers le pare-feu 2). Après avoir détecté un nouveau message, elle le récupère, effectue un traitement initial si besoin et le place dans la base de données MessageBox.  
  
4.  Une instance de l'hôte de traitement, qui a un abonnement au message, le récupère dans la base de données MessageBox, effectue un traitement supplémentaire, puis replace le message dans la base de données MessageBox.  
  
5.  Une instance de l'hôte In-process, qui a un adaptateur d'envoi FTP, récupère le message dans la base de données MessageBox. Le message passe par un traitement final dans le pipeline d'envoi, puis est envoyé au serveur FTP à travers le pare-feu 2.  
  
6.  Le serveur FTP achemine ensuite le message à travers le pare-feu 1 jusqu'au partenaire ou au client.  
  
## <a name="step-2-create-and-analyze-the-threat-model-ftp-adapter-scenario"></a>Étape 2. Créer et analyser le modèle des menaces (scénario de l’adaptateur FTP)  
 Cette section présente les résultats de l'analyse du modèle des menaces pour le scénario de l'adaptateur FTP dans un exemple d'architecture.  
  
-   **Identifier les Points d’entrée, les limites de confiance et les flux de données -** consultez les informations générales décrites précédemment à l’étape 1 et dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
-   **Créer une liste des menaces identifiées -** nous avons utilisé la catégorisation suivante pour toutes les entrées du diagramme pour identifier les menaces potentielles pour le scénario : **S**urpation identifier, **T** ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges. Le tableau suivant répertorie les menaces qui ont été identifiées lors de l'utilisation de l'adaptateur FTP pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 1 liste des menaces identifiées**  
  
|Menace| Description|Actif|Impact|  
|------------|-----------------|-----------|------------|  
|Protocole FTP non sécurisé|L'ID et le mot de passe utilisateur du protocole FTP sont envoyés en texte clair. Un utilisateur malveillant surveille peut-être le réseau dans le but d'accéder à des informations d'identification. Les données sont exposées.|Informations d’identification de l’utilisateur|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Divulgation d'informations|  
|Le serveur FTP est vulnérable face aux attaques de serveur DHCP non autorisé|Si l'URI ne contient pas le mot de passe de l'utilisateur mais que le mot de passe est spécifié dans le gestionnaire, il sera envoyé, au moment de l'exécution, à partir du gestionnaire au serveur FTP. Si un serveur FTP non autorisé écoute des appels d'authentification, celui-ci peut employer cette méthode pour voler des mots de passe. Une solution consiste à activer/désactiver l'utilisation du mot de passe au niveau du gestionnaire.|Serveur FTP|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Divulgation d'informations|  
  
## <a name="step-3-review-threats-ftp-adapter-scenario"></a>Étape 3. Examen des menaces (scénario de l’adaptateur FTP)  
 Cette section présente les résultats de l'analyse des risques réalisée sur les menaces identifiées pour le scénario de l'adaptateur FTP dans un exemple d'architecture. Après la principale menace réunion sur le modèle, nous avons passé en revue les menaces et utilisé l’espace utilisé des catégories pour identifier le risque pour chaque menace un impact sur les éléments suivants : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **A**tteinte des utilisateurs et **D**étectabilité.  
  
 Le tableau suivant répertorie les degrés de risque pour les menaces qui ont été identifiées lors de l'utilisation de l'adaptateur FTP pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 2 degrés de risque pour les menaces identifiées**  
  
|Menace|Impact|Dégâts potentiels|Reproductibilité|Exploitabilité|Atteinte des utilisateurs|Détectabilité|Exposition au risque|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|Protocole FTP non sécurisé|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Divulgation d'informations|9|9|2|10|5|7|  
|Le serveur FTP est vulnérable face aux attaques de serveur DHCP non autorisé|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Divulgation d'informations|5|5|2|10|5|5.4|  
  
## <a name="step-4-identify-mitigation-techniques-ftp-adapter-scenario"></a>Étape 4. Identifier les Techniques de prévention (scénario de l’adaptateur FTP)  
 Cette section présente certaines techniques de prévention des menaces identifiées pour le scénario de l'adaptateur FTP dans un exemple d'architecture.  
  
 Le tableau suivant répertorie les techniques et technologies de prévention des menaces qui ont été identifiées lors de l'utilisation de l'adaptateur FTP pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 3 techniques de prévention et technologies**  
  
|Menace|Impact|Exposition au risque|Techniques et technologies de prévention|  
|------------|------------|-------------------|--------------------------------------------|  
|Protocole FTP non sécurisé|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Divulgation d'informations|7|L'utilisation de l'adaptateur FTP doit être effectuée au sein d'un environnement sécurisé et par l'intermédiaire d'une ligne sécurisée.|  
|Le serveur FTP est vulnérable face aux attaques de serveur DHCP non autorisé|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Divulgation d'informations|5.4|Il est recommandé de placer le serveur FTP distant dans un emplacement sécurisé. Pour réduire le nombre des attaques de serveur DHCP non autorisé, vous devez garantir la sécurité physique et celle du réseau de ce serveur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse du modèle](../core/threat-model-analysis.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)