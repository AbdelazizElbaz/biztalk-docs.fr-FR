---
title: "Fonctionne de l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7789316d-f2c4-4018-a8e8-dd9359f1664f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe7d7b473482c432c8e3ae9ca48cab414a9e9573
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-dynamic-resolution-sample-works"></a>Fonctionne de l’exemple de résolution dynamique
L’exemple de résolution dynamique utilise le composant de pipeline désassembleur de répartiteur ESB pour tous les exemples de messagerie décrits dans la section précédente.  
  
 Pour les scénarios de messagerie unidirectionnels, l’exemple résout le point de terminaison à l’aide de la méthode statique, BRE ou programme de résolution de XPATH et transmet les requêtes du protocole de fichier au fichier, FTP ou MQSeries.  
  
 Pour les scénarios de messagerie bidirectionnelles, l’exemple résout le point de terminaison à l’aide de la méthode statique, BRE, UDDI ou programme de résolution de XPATH et transmet les requêtes du protocole SOAP à partir de SOAP ou WCF-BasicHttp. En outre, les exemples résoudre et exécutent des mappages de Microsoft BizTalk à l’aide du résolveur BRE, qui utilise des faits contenues dans les propriétés de contexte de message et le corps du message pour déterminer le résultat de la résolution.  
  
 Le résultat du processus de résolution est que tous les exemples bidirectionnelles envoyer son message à l’architecture ESB. Service Web de CanadianServices à http://localhost/ESB.CanadianServices/SubmitPOService.asmx. En outre, en fonction du résultat de la résolution, l’exemple exécute la **submitOrder** ou **submitPurchase** action. En outre, le composant de pipeline désassembleur de répartiteur ESB exécute dynamiquement un mappage BizTalk, selon le texte spécifié ou l’action exécutée.  
  
 La figure 1 illustre que les pipelines configurés pour le DynamicResolutionReqResp_SOAP l’emplacement de réception.  
  
 ![Pipelines de résolution dynamique](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "§ 6-DynamicResolutionPipelines")  
  
 **Figure 1**  
  
 **Les pipelines configurées de la DynamicResolutionReqResp_SOAP réception de l’application d’exemple de résolution dynamique**  
  
 La figure 2 illustre les propriétés de chaque instance du composant ESBReceiveXML qui utilise le désassembleur de répartiteur ESB.  
  
 ![Résolution dynamique de réception XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "§ 6-DynamicResolutionReceiveXML")  
  
 **Figure 2**  
  
 **Les propriétés de chaque instance pour les composants dans le pipeline ESBReceiveXML de l’application d’exemple de résolution dynamique**  
  
 Les propriétés suivantes sont présentées dans la Figure 2 :  
  
-   **Activé**. Cette propriété détermine si le pipeline est actif. Si la valeur est **False**, messages passent sans traitement.  
  
-   **Point de terminaison**. Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution à charger, et spécifie la configuration de point de terminaison.  
  
-   **MapName**. Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution pour charger et le mappage BizTalk à exécuter. Il peut être le nom qualifié complet d’un mappage au lieu d’une chaîne de connexion du programme de résolution.  
  
-   **Valider**. Lorsque la valeur **True** (paramètre par défaut), le désassembleur de répartiteur ESB composant fait en sorte que le service de Transformation d’ESB pour valider le message source par rapport au schéma source défini dans le plan est résoudre et les exécuter.  
  
 Figure 3 illustre les propriétés de chaque instance du composant ESBSendPassthrough qui utilise le répartiteur ESB.  
  
 ![Résolution dynamique d’envoi Passthrough](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "§ 6-DynamicResolutionSendPassthrough")  
  
 **Figure 3**  
  
 **Les propriétés de chaque instance pour les composants dans le pipeline ESBSendPassthrough de l’application d’exemple de résolution dynamique**  
  
 Les propriétés suivantes sont présentées dans la Figure 3 :  
  
-   **Activé**. Cette propriété détermine si le pipeline est actif. Si la valeur est **False**, messages passent sans traitement.  
  
-   **Point de terminaison**. Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution de chargement et la configuration de point de terminaison.  
  
-   **MapName**. Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution pour charger et le mappage BizTalk à exécuter. Un nom qualifié complet d’un mappage peut être utilisé à la place la chaîne de connexion d’un programme de résolution.  
  
-   **Valider**. Lorsque la valeur **True** (paramètre par défaut), le désassembleur de répartiteur ESB composant fait en sorte que le service de Transformation d’ESB pour valider le message source par rapport au schéma source défini dans le plan est résoudre et les exécuter.