---
title: "Exemple TMA : Adaptateur de fichier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- DFD, File adapters
- File adapters, TMA
- examples, File adapters
- security examples [TMA], File adapters
ms.assetid: bcb862c0-fe02-4335-8b59-242d28049e3f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b0a5bfe1cce0db07ef26a8d71cc6795cd49202f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-file-adapter"></a>Exemple menaces : Adaptateur de fichier
Cette rubrique présente l'analyse du modèle des menaces pour le scénario de l'adaptateur FILE dans un exemple d'architecture. L’illustration suivante montre l’exemple d’architecture pour le scénario de l’adaptateur File.  
  
 **Figure 1 exemple d’architecture pour le scénario de l’adaptateur File**  
  
 ![Exemple d’architecture pour l’adaptateur File](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")  
  
## <a name="step-1-collect-background-information-file-adapter-scenario"></a>Étape 1. Collecter des informations générales (scénario de l’adaptateur de fichier)  
 Cette section présente le diagramme de flux de données pour le scénario de l'adaptateur FILE dans un exemple d'architecture.  
  
 Toutes les autres informations d’arrière-plan est le même pour tous nos scénarios d’utilisation et est décrite précédemment dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).  
  
### <a name="data-flow-diagram"></a>Diagramme de flux de données  
 La figure suivante illustre le diagramme de flux de données pour l'exemple d'architecture lors de l'utilisation de l'adaptateur FILE.  
  
 **Figure 2 DFD pour l’exemple d’architecture du scénario de l’adaptateur de fichier**  
  
 ![Exemple d’architecture pour DFD](../core/media/tdi-sec-refarch-dfd-file.gif "TDI_Sec_RefArch_DFD_FILE_")  
  
 Le flux de données est le suivant :  
  
1.  Un partenaire place un message (via le pare-feu 1) dans le serveur FILE dans le réseau de périmètre intranet.  
  
2.  Une instance d'un hôte In-process pour l'adaptateur de réception FILE interroge régulièrement le serveur FILE pour les nouveaux messages (via le pare-feu 2). Après avoir détecté un nouveau message, elle le récupère, effectue un traitement initial si besoin et le place dans la base de données MessageBox.  
  
3.  Une instance de l'hôte de traitement, qui a un abonnement au message, le récupère dans la base de données MessageBox, effectue un traitement supplémentaire, puis replace le message dans la base de données MessageBox.  
  
4.  Une instance de l'hôte In-process, qui a un adaptateur d'envoi FILE, récupère le message dans la base de données MessageBox. Le message passe par un traitement final dans le pipeline d'envoi, puis est envoyé au serveur FILE via le pare-feu 2.  
  
5.  Le partenaire récupère le message à partir du serveur FILE.  
  
## <a name="step-2-create-and-analyze-the-threat-model-file-adapter-scenario"></a>Étape 2. Créer et analyser le modèle des menaces (scénario de l’adaptateur File)  
 Cette section présente les résultats de l'analyse du modèle des menaces pour le scénario de l'adaptateur FILE dans un exemple d'architecture.  
  
-   **Identifier les Points d’entrée, les limites de confiance et les flux de données -** consultez des informations générales décrites précédemment dans « Collecter en arrière-plan des informations pour scénario adaptateur File » et « En arrière-plan des informations pour tous les scénarios ».  
  
-   **Créer une liste des menaces identifiées -** nous avons utilisé la catégorisation suivante pour toutes les entrées du diagramme pour identifier les menaces potentielles pour le scénario : **S**urpation identifier, **T** ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges. Le tableau suivant répertorie les menaces qui ont été identifiées lors de l'utilisation de l'adaptateur FILE pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 1 liste d’identifie les menaces**  
  
|Menace| Description|Actif|Impact|  
|------------|-----------------|-----------|------------|  
|Un utilisateur non autorisé peut récupérer les messages à partir du dossier de dépôt de fichiers|Si vous n'avez défini aucune liste de contrôle d'accès discrétionnaire (DACL) renforcée pour les dossiers que l'adaptateur FILE utilise, un utilisateur non autorisé peut déposer des messages dans l'emplacement de réception des fichiers ou en récupérer à partir de l'emplacement d'envoi des fichiers.|Corps du message|Falsification de données<br /><br /> Divulgation d'informations|  
|Un utilisateur non autorisé peut envoyer des messages à BizTalk Server|Si un utilisateur dispose d'autorisations en écriture sur le dossier de fichiers à partir duquel BizTalk Server récupère les messages, un utilisateur non autorisé peut envoyer des messages à BizTalk Server.|Corps du message|Déni de service<br /><br /> Élévation de privilèges|  
  
## <a name="step-3-review-threats-file-adapter-scenario"></a>Étape 3. Examen des menaces (scénario de l’adaptateur File)  
 Cette section présente les résultats de l'analyse des risques réalisée sur les menaces identifiées pour le scénario de l'adaptateur FILE dans un exemple d'architecture. Après la principale menace réunion sur le modèle, nous avons passé en revue les menaces et les catégories d’impact suivants permettent d’identifier les risques pour chaque menace : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **A**tteinte des utilisateurs et **D**étectabilité.  
  
 Le tableau suivant répertorie les degrés de risque pour les menaces que nous avons identifiées lors de l'utilisation de l'adaptateur FILE pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 2 degrés de risque pour les menaces identifiées**  
  
|Menace|Impact|Dégâts potentiels|Reproductibilité|Exploitabilité|Atteinte des utilisateurs|Détectabilité|Exposition au risque|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|Un utilisateur non autorisé peut récupérer les messages à partir du dossier de dépôt de fichiers|Falsification de données<br /><br /> Divulgation d'informations|4|7|5|4|6|5.2|  
|Un utilisateur non autorisé peut envoyer des messages à BizTalk Server|Déni de service<br /><br /> Élévation de privilèges|4|7|5|4|5|5.2|  
  
## <a name="step-4-identify-mitigation-techniques-file-adapter-scenario"></a>Étape 4. Identifier les Techniques de prévention (scénario de l’adaptateur File)  
 Cette section présente certaines techniques de prévention des menaces identifiées pour le scénario de l'adaptateur FILE dans un exemple d'architecture.  
  
 Le tableau suivant répertorie les techniques et technologies de prévention des menaces qui ont été identifiées lors de l'utilisation de l'adaptateur FILE pour envoyer et recevoir des messages vers et depuis BizTalk Server.  
  
 **Tableau 3 techniques de prévention et technologies**  
  
|Menace|Impact|Exposition au risque|Techniques et technologies de prévention|  
|------------|------------|-------------------|--------------------------------------------|  
|Un utilisateur non autorisé peut récupérer les messages à partir du dossier de dépôt de fichiers|Falsification de données<br /><br /> Divulgation d'informations|5.2|Pour le dossier à partir duquel BizTalk Server récupère les messages, utilisez une liste de contrôle d'accès discrétionnaire (DACL) renforcée comme suit :<br /><br /> -Pour le compte de service pour l’instance d’hôte de l’hôte qui exécute l’adaptateur de réception, définir en lecture, écriture, supprimer des fichiers et supprimer des autorisations de fichiers et sous-dossiers dans le répertoire à partir de laquelle l’emplacement de réception de fichier récupère les messages.<br />-Pour l’application qui dépose des fichiers dans ce dossier ou d’un utilisateur externe, jeu d’autorisations d’écriture.<br />-Pour le groupe d’administrateurs BizTalk, définissez un contrôle total.<br /><br /> Pour le dossier dans lequel BizTalk Server dépose les messages, utilisez une liste de contrôle d'accès discrétionnaire (DACL) renforcée comme suit :<br /><br /> -Pour le compte de service pour l’instance d’hôte de l’hôte qui exécute l’adaptateur d’envoi, définissez les autorisations d’écriture.<br />-Pour l’application qui dépose des fichiers dans ce dossier ou d’un utilisateur externe, jeu d’autorisations de lecture.<br />-Pour le groupe d’administrateurs BizTalk, définissez un contrôle total.|  
|Un utilisateur non autorisé peut envoyer des messages à BizTalk Server|Déni de service<br /><br /> Élévation de privilèges|5.2|Définissez les listes de contrôle d'accès discrétionnaire (DACL) renforcées dans les répertoires de dépôt de l'emplacement de réception (comme indiqué précédemment).|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse du modèle](../core/threat-model-analysis.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)