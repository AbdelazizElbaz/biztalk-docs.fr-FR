---
title: "Considérations lors de l’utilisation de BizTalk Server sur un système d’exploitation Windows 64 bits | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac630f55-7ebe-4b93-bf98-70b00788520f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4c6ac3b8a3104e1c96b2dc9ebd880489d3c9833
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system"></a>Considérations lors de l’utilisation de BizTalk Server sur un système d’exploitation Windows 64 bits
Lorsque vous utilisez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un système d’exploitation de Windows 64 bits, assurez-vous que vous tenez compte des problèmes décrits dans cette rubrique. Pour les questions fréquemment posées relatives à la prise en charge de 64 bits de Microsoft BizTalk Server, consultez [prise en charge BizTalk Server 64 bits](http://go.microsoft.com/fwlink/?LinkID=155306) (http://go.microsoft.com/fwlink/?LinkID=155306).  
  
## <a name="modify-the-process-memory-usage-throttling-threshold"></a>Modifier l’utilisation de mémoire de processus seuil de limitation  
 Par défaut, le **traiter l’utilisation de la mémoire** seuil de limitation de l’hôte est défini sur 25. Si cette valeur est dépassée et l’utilisation de mémoire de processus BizTalk est plus de 300 Mo, une condition de limitation peut se produire. Sur un serveur 64 bits, vous pouvez augmenter cette valeur à 100. Cela permet une plus grande consommation de mémoire par le processus BizTalk avant que la limitation se produit. Pour obtenir des instructions sur la modification de l’hôte de l’utilisation de mémoire de processus seuil de limitation, consultez [comment modifier les paramètres de limitation d’hôte par défaut](http://go.microsoft.com/fwlink/?LinkId=157210) (http://go.microsoft.com/fwlink/?LinkId=157210).  
  
> [!NOTE]  
>  La mémoire de processus maximale disponible est limitée à la taille de l'espace d'adressage de 2 Go pour les besoins de ce calcul, même si le système dispose de plus de 2 Go de mémoire physique. Cette limite est utilisée pour les besoins du calcul sur les systèmes 32 et 64 bits. Afin d’éviter les erreurs de mémoire insuffisante, il est recommandé que vous ne spécifiez pas une valeur qui permettra à hôte mémoire supérieure à 1,54 Go lors de l’exécution d’une version 32 bits de BizTalk Server, indépendamment de si BizTalk Server est installé sur un 32 bits ou 64 bits sy de fonctionnement de l’instance stem. Par exemple, si vous spécifiez pour ce paramètre une valeur comprise entre 1 et 100 afin de déclencher une limitation basée sur le pourcentage de mémoire de processus utilisée, n'entrez pas de valeur supérieure à 75 (.75 * 2GB = 1,54 Go). Si vous spécifiez une valeur supérieure à 100 pour ce paramètre pour déclencher une limitation basée sur le nombre spécifié en Mo, n’entrez pas une valeur supérieure à 1536.If vous exécutez une version 64 bits de BizTalk Server, spécifiez une valeur ou 100 (100 %) soit 2048 (2 Go) pour lancer  la limitation lorsque la mémoire de processus maximale disponible de 2 Go est utilisée.  
  
## <a name="adapters-that-do-not-support-64-bit-hosts"></a>Adaptateurs qui ne prennent pas en charge les ordinateurs hôtes 64 bits  
 Les adaptateurs suivants ne sont pas pris en charge pour s’exécuter sur des instances d’hôte 64 bits :  
  
-   Adaptateur FTP  
  
-   Adaptateur POP3  
  
 Assurez-vous que vous exécutez ces adaptateurs dans une instance d’hôte 32 bits.  
  
## <a name="configure-the-mimesmime-encoder-to-run-in-32-bit-mode"></a>Configurer l’encodeur MIME/SMIME pour s’exécuter en mode 32 bits  
 Dans BizTalk Server, les matrices de composant de pipeline Encodeur MIME/SMIME n'ont pas une prise en charge 64 bits native. Il doit donc être exécuté dans un processus d'émulation 32 bits (WOW64). Cela implique que l'instance de l'hôte où s'exécute ce composant de codage (ou le pipeline d’envoi dont il fait partie) s'exécute dans un mode d'émulation 32 bits. Tenez compte des implications de cette restriction, notamment concernant les performances, pour les autres éléments de BizTalk qui s'exécutent dans cette même instance de l'hôte.