---
title: Erreurs de Registre | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5bf2cd-f807-4083-8687-4416a2ee2908
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c84ec2a1082f431fef8e06357f14cc9b621c6a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="registry-errors"></a>Erreurs en relation avec le Registre
Informations sur le diagnostic et résolution des erreurs de Registre WCF.  

## <a name="failed-to-access-the-registry"></a>Échec de l'accès au Registre
  
||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d’ouvrir HKLM\\{0}.|  
  
### <a name="explanation"></a>Explication  
 Cette erreur indique l'échec de l'accès au Registre.  
  
### <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que vous disposez d'un accès en lecture au Registre Pour accéder au Registre, assurez-vous de disposer d'autorisations Administrateur ou contactez l'administrateur de l'ordinateur.
 
## <a name="failed-to-obtain-biztalk-install-path"></a>Impossible d'obtenir le chemin d'installation de BizTalk
  
||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d’obtenir le chemin d’installation de BizTalk à partir de HKLM\\{0}\\{{1}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique l'échec de l'accès au Registre et une valeur de clé incorrecte.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que vous disposez d'un accès en lecture au Registre et que la valeur de la clé est correcte. Pour accéder au Registre, assurez-vous de disposer d'autorisations Administrateur ou contactez l'administrateur de l'ordinateur. 