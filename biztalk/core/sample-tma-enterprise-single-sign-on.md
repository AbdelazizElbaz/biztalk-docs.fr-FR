---
title: "Exemple de menaces : Enterprise Single Sign-On | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], SSO
- architecture, examples
- SSO, examples
- SSO, TMA
- DFD, SSO
- examples, SSO
- examples, TMA
ms.assetid: c2c15b1b-54f3-4d1a-b3d8-6679abd41ccb
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb57e7b22680844e3ddb18481aa76002df78b013
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-enterprise-single-sign-on"></a>Exemple de menaces : Enterprise Single Sign-On
Cette rubrique présente l'analyse du modèle des menaces pour le scénario d'authentification unique de l'entreprise dans un exemple d'architecture.  
  
 La figure suivante illustre l'exemple d'architecture de base, qui inclut le scénario d'authentification unique de l'entreprise.  
  
 **Figure 1 architecture d’exemple de Base qui inclut le scénario Enterprise Single Sign-On**  
  
 ![Composants de l’architecture de base](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")  
  
## <a name="step-1-collect-background-information-enterprise-single-sign-on-scenario"></a>Étape 1. Collecter des informations générales (Enterprise seul scénario d’authentification)  
 Cette section présente le diagramme de flux de données pour l'utilisation du scénario d'authentification unique de l'entreprise lorsque vous mappez les informations d'identification Windows à celles que vous utilisez pour la connexion à un réseau principal.  
  
 Toutes les autres informations d’arrière-plan est le même pour tous nos scénarios d’utilisation et est décrite précédemment dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
### <a name="data-flow-diagram"></a>Diagramme de flux de données  
 La figure suivante illustre le diagramme de flux de données pour le scénario d'authentification unique de l'entreprise.  
  
 **Figure 2 DFD pour le scénario Enterprise Single Sign-On**  
  
 ![DFD pour l’authentification unique de l’entreprise &#45; sur](../core/media/tdi-sec-refarch-dfd-sso.gif "TDI_Sec_RefArch_DFD_SSO")  
  
 Le flux de données est le suivant :  
  
1.  L'utilisateur ou l'application se connecte avec les informations d'identifications Windows.  
  
2.  L'authentification unique de l'entreprise utilise les informations d'identification Windows pour demander les informations d'identification du réseau principal.  
  
3.  L'authentification unique de l'entreprise mappe les informations d'identification Windows aux informations d'identification principales stockées dans la base de données SSO.  
  
4.  L'authentification unique de l'entreprise récupère les informations d'identification principales et utilise celles-ci pour connecter l'utilisateur ou l'application au réseau principal.  
  
## <a name="step-2-create-and-analyze-the-threat-model-enterprise-single-sign-on-scenario"></a>Étape 2. Créer et analyser le modèle des menaces (Enterprise l’authentification unique)  
 Cette section présente les résultats de l'analyse du modèle des menaces pour le scénario de l'authentification unique de l'entreprise dans un exemple d'architecture.  
  
-   **Identifier les Points d’entrée, les limites de confiance et les flux de données** -consultez les informations générales décrites précédemment à l’étape 1 et dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
-   **Créer une liste des menaces identifiées** -nous avons utilisé la catégorisation suivante pour toutes les entrées du diagramme pour identifier les menaces potentielles pour le scénario : **S**urpation identifier, **T** ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges. Le tableau suivant répertorie les menaces qui ont été identifiées lors de l'utilisation de l'authentification unique de l'entreprise pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 1 liste des menaces identifiées**  
  
|Menace| Description|Actif|Impact|  
|------------|-----------------|-----------|------------|  
|Le serveur de secret principal constitue un point faible|Si un utilisateur malveillant compromet le serveur de secret principal, l'ordinateur d'authentification unique est incapable de chiffrer les informations d'identification (il reste capable de déchiffrer les informations d'identification).|BizTalk Server et l'environnement d'authentification unique|Déni de service|  
|Un utilisateur malveillant peut usurper l'identité d'un client ou d'un serveur|Si un client ou un serveur exécute Windows sans l'authentification NTLM, un utilisateur malveillant peut usurper l'identité d'un client ou d'un serveur.|BizTalk Server et l'environnement d'authentification unique|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Répudiation<br /><br /> Divulgation d'informations<br /><br /> Déni de service<br /><br /> Élévation de privilèges|  
|Un utilisateur malveillant peut falsifier les données lorsqu'elles transitent d'un serveur à un autre.|La communication entre les serveurs s'effectue en texte clair, et un utilisateur malveillant peut lire les données lors de leur transit.|data|Falsification de données<br /><br /> Divulgation d'informations|  
  
## <a name="step-3-review-threats-enterprise-single-sign-on-scenario"></a>Étape 3. Examen des menaces (Enterprise l’authentification unique)  
 Cette section présente les résultats de l'analyse des risques réalisée sur les menaces identifiées pour le scénario d'authentification unique de l'entreprise BizTalk dans l'architecture de référence. Après la principale menace réunion sur le modèle, nous avons passé en revue les menaces et utilisé l’espace utilisé des catégories pour identifier le risque pour chaque menace un impact sur les éléments suivants : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **A**tteinte des utilisateurs et **D**étectabilité.  
  
 Le tableau suivant répertorie les degrés de risque pour les menaces qui ont été identifiées lors de l'utilisation de l'authentification unique de l'entreprise pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 2 niveau de risque de menaces identifiées**  
  
|Menace|Impact|Dégâts potentiels|Reproductibilité|Exploitabilité|Atteinte des utilisateurs|Détectabilité|Exposition au risque|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|Le serveur de secret principal constitue un point faible|Déni de service|2|3|2|1|2|2|  
|Un utilisateur malveillant peut usurper l'identité d'un client ou d'un serveur|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Répudiation<br /><br /> Divulgation d'informations<br /><br /> Déni de service<br /><br /> Élévation de privilèges|3|2|2|2|1|2|  
|Un utilisateur malveillant peut falsifier les données lorsqu'elles transitent d'un serveur à un autre.|Falsification de données<br /><br /> Divulgation d'informations|3|1|1|2|1|1.6|  
  
## <a name="step-4-identify-mitigation-techniques-enterprise-single-sign-on-scenario"></a>Étape 4. Identifier les Techniques de prévention (Enterprise l’authentification unique)  
 Cette section présente certaines techniques de prévention des menaces identifiées pour le scénario de l'authentification unique de l'entreprise dans un exemple d'architecture.  
  
 Le tableau suivant répertorie les techniques et technologies de prévention des menaces qui ont été identifiées lors de l'utilisation de l'authentification unique de l'entreprise.  
  
 **Tableau 3 techniques de prévention et technologies**  
  
|Menace|Impact|Exposition au risque|Techniques et technologies de prévention|  
|------------|------------|-------------------|--------------------------------------------|  
|Le serveur de secret principal constitue un point faible|Déni de service|2|Utilisez une configuration de cluster active/passive pour le serveur de secret principal.<br /><br /> Pour plus d’informations sur le serveur de secret principal de clustering, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).|  
|Un utilisateur malveillant peut usurper l'identité d'un client ou d'un serveur|Usurpation d'identité<br /><br /> Falsification de données<br /><br /> Répudiation<br /><br /> Divulgation d'informations<br /><br /> Déni de service<br /><br /> Élévation de privilèges|2|Si votre réseau prend en charge l'authentification Kerberos, vous devez inscrire tous les serveurs SSO. Lorsque vous utilisez l'authentification Kerberos entre le serveur de secret principal et la base de données SSO, vous devez configurer des noms principaux de service (SPN) sur le serveur SQL où se trouve la base de données SSO.<br /><br /> Pour plus d’informations sur la configuration des noms principaux de Service, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=61374](http://go.microsoft.com/fwlink/?LinkId=61374).|  
|Un utilisateur malveillant peut falsifier les données lorsqu'elles transitent d'un serveur à un autre.|Falsification de données<br /><br /> Divulgation d'informations|1.6|Utilisez le protocole IPSec (Internet Protocol security) ou SSL (Secure Sockets Layer) entre tous les serveurs SSO et la base de données SSO.<br /><br /> Pour plus d’informations sur le protocole SSL, consultez le site Web de support technique et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkID=189708](http://go.microsoft.com/fwlink/?LinkID=189708).<br /><br /> Pour plus d’informations sur l’utilisation de SSL entre tous les serveurs SSO et la base de données SSO, consultez [comment activer SSL pour SSO](../core/how-to-enable-ssl-for-sso.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse du modèle](../core/threat-model-analysis.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)