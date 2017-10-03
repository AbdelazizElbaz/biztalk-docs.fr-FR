---
title: "Limitations de l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, limitations of
- IDOC, sending an IDOC to an SAP system
ms.assetid: 1ca1e0cf-7ae7-4a8b-8363-e5f3746e8e26
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d392178cd49918151f0ad86c73a5fcba712d6b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-mysap-business-suite"></a>Limitations de l’adaptateur BizTalk pour mySAP Business Suite

## <a name="limitations-list"></a>Liste des limitations
Les éléments suivants sont connus des limitations de la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:  
  
-   Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] n’est pas compatible avec l’adaptateur Microsoft BizTalk pour mySAP Business Suite, la version précédente de l’adaptateur. Cette version de l’adaptateur ne prend pas en charge les envoyer et recevoir des messages ayant des schémas générés à l’aide de la version antérieure de l’adaptateur.  
  
-   Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge les normes RFC avec les types de paramètre complexe, y compris les types de table (hiérarchiques) ITAB II.  
  
-   Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge les RFC ayant des types ABAP personnalisés.  
  
-   En raison de problèmes de délai d’attente un traitement par la bibliothèque cliente sous-jacente, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.  
  
-   Si vous modifiez l’heure système de l’ordinateur qui exécute l’hôte BizTalk Server, l’heure n’est pas automatiquement actualisé dans l’hôte BizTalk Server. Cela peut entraîner un comportement incorrect des opérations entrantes qui utilisent le port de réception de BizTalk Server. Pour résoudre ce problème, vous devez redémarrer l’instance d’hôte qui possède un port de réception après avoir modifié l’heure système de l’ordinateur exécutant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)